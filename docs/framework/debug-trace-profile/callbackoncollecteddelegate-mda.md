---
title: "callbackOnCollectedDelegate MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MDAs (managed debugging assistants), garbage collection"
  - "managed debugging assistants (MDAs), callback on collected delegates"
  - "MDAs (managed debugging assistants), callback on collected delegates"
  - "callback on delegate after garbage collection"
  - "callbackOnCollectedDelegate MDA"
  - "managed debugging assistants (MDAs), garbage collection"
  - "call back collected delegates"
  - "garbage collection, run-time errors"
  - "delegates [.NET Framework], garbage collection"
ms.assetid: 398b0ce0-5cc9-4518-978d-b8263aa21e5b
caps.latest.revision: 15
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 15
---
# callbackOnCollectedDelegate MDA
L'Assistant Débogage managé \(MDA\) `callbackOnCollectedDelegate` est activé si un délégué est marshalé du code managé vers du code non managé en tant que pointeur de fonction et si un rappel est placé sur ce pointeur de fonction après la récupération du délégué par le garbage collector.  
  
## Symptômes  
 Des violations d'accès se produisent lors des tentatives d'appel de code managé par les pointeurs de fonction obtenus par des délégués managés.  Ces échecs, qui ne sont pas des bogues du common language runtime \(CLR\), peuvent pourtant y ressembler, car la violation d'accès se produit dans le code CLR.  
  
 Les échecs ne surviennent pas de façon cohérente : tantôt l'appel sur le pointeur de fonction aboutit, tantôt il échoue.  Un échec peut se produire dans une situation de surcharge uniquement ou sur un nombre aléatoire de tentatives.  
  
## Cause  
 Le délégué à partir duquel le pointeur de fonction a été créé et ensuite exposé au code non managé a été récupéré par le garbage collector.  Quand le composant non managé tente d'appeler sur le pointeur de fonction, il génère une violation d'accès.  
  
 L'échec est aléatoire, car il dépend du moment où l'opération garbage collection se produit.  Si un délégué peut faire l'objet d'une opération garbage collection, celle\-ci peut avoir lieu après le rappel et, dans ce cas, l'appel aboutit.  Dans d'autres cas où l'opération garbage collection se produit avant le rappel, le rappel génère une violation d'accès et le programme s'arrête.  
  
 La probabilité d'avoir un échec dépend du laps de temps entre le marshaling du délégué et le rappel sur le pointeur de fonction, ainsi que de la fréquence des opérations garbage collection.  L'échec est sporadique si le laps de temps entre le marshaling du délégué et le rappel résultant est court.  Cela est généralement le cas si la méthode non managée qui reçoit le pointeur de fonction ne l'enregistre pas pour une utilisation ultérieure, mais le rappelle immédiatement pour terminer son opération avant d'être retournée.  De la même façon, davantage d'opérations garbage collection se produisent quand un système est en surcharge, ce qui rend plus probable l'exécution d'une opération garbage collection avant le rappel.  
  
## Résolution  
 Quand un délégué a été marshalé en tant que pointeur de fonction non managé, le garbage collector ne peut pas effectuer le suivi de sa durée de vie.  Votre code doit alors conserver une référence au délégué pendant toute la durée de vie du pointeur de fonction non managé.  Pour cela, vous devez d'abord identifier le délégué qui a été collecté.  Si l'Assistant Débogage managé est activé, il fournit le nom de type du délégué.  Utilisez ce nom pour rechercher votre code d'appel de code non managé ou les signatures COM qui transmettent ce délégué au code non managé.  Le délégué incriminé est transmis par l'un de ces sites d'appel.  Vous pouvez également activer l'Assistant Débogage managé `gcUnmanagedToManaged` pour forcer une opération garbage collection avant chaque rappel dans le runtime.  Vous êtes ainsi certain qu'une opération garbage collection se produit toujours avant le rappel.  Une fois que vous savez quel délégué a été collecté, modifiez votre code pour conserver une référence à ce délégué dans le code managé pendant toute la durée de vie du pointeur de fonction non managé ayant été marshalé.  
  
## Effet sur le runtime  
 Quand les délégués sont marshalés en tant que pointeurs de fonction, le runtime alloue un thunk qui effectue la transition du code non managé au code managé.  Ce thunk est en fait ce que le code non managé appelle avant que le délégué managé soit finalement appelé.  Si l'Assistant Débogage managé `callbackOnCollectedDelegate` n'est pas activé, le code de marshaling non managé est supprimé quand le délégué est collecté.  Si l'Assistant Débogage managé `callbackOnCollectedDelegate` est activé, le code de marshaling non managé n'est pas immédiatement supprimé quand le délégué est collecté.  Au lieu de cela, les 1 000 dernières instances restent actives par défaut et sont modifiées pour activer l'Assistant Débogage managé au moment de l'appel.  Le thunk est finalement supprimé après la collecte de 1 001 délégués marshalés supplémentaires.  
  
## Sortie  
 L'Assistant Débogage managé signale le nom de type du délégué qui a été collecté avant une tentative de rappel sur son pointeur de fonction non managé.  
  
## Configuration  
 L'exemple suivant montre les options de configuration de l'application.  Il définit le nombre des thunks que l'Assistant Débogage managé garde actifs à 1 500.  La valeur `listSize` par défaut est 1 000, le minimum 50 et le maximum 2 000.  
  
```  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## Exemple  
 L'exemple suivant illustre une situation qui peut activer cet Assistant Débogage managé :  
  
```  
// Library.cpp : Defines the unmanaged entry point for the DLL application.  
#include "windows.h"  
#include "stdio.h"  
  
void (__stdcall *g_pfTarget)();  
  
void __stdcall Initialize(void __stdcall pfTarget())  
{  
    g_pfTarget = pfTarget;  
}  
  
void __stdcall Callback()  
{  
    g_pfTarget();  
}  
// ---------------------------------------------------  
// C# Client  
using System;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public delegate void DCallback();  
  
    public static void Main()  
    {  
        new Entry();  
        Initialize(Target);  
        GC.Collect();  
        GC.WaitForPendingFinalizers();  
        Callback();  
    }  
  
    public static void Target()  
    {          
    }  
  
    [DllImport("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Initialize(DCallback pfDelegate);  
  
    [DllImport ("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Callback();  
  
    ~Entry() { Console.Error.WriteLine("Entry Collected"); }  
}  
```  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md)   
 [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)