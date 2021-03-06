---
title: Opérations verrouillées
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Interlocked class, about Interlocked class
- threading [.NET Framework], Interlocked class
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 069a95656e7ceaf454c01c47d61ff391bcbed2fe
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46538883"
---
# <a name="interlocked-operations"></a>Opérations verrouillées

La classe <xref:System.Threading.Interlocked?displayProperty=nameWithType> fournit des méthodes qui synchronisent l’accès à une variable partagée par plusieurs threads. Les threads de processus différents peuvent utiliser ce mécanisme si la variable se trouve dans la mémoire partagée. Les opérations verrouillées sont atomiques, autrement dit, l’opération entière est une unité qui ne peut pas être interrompue par une autre opération sur la même variable. Cela est important dans les systèmes d’exploitation multithreading préemptifs, où un thread peut être suspendu après le chargement d’une valeur à partir d’une adresse de mémoire, mais avant d’avoir la possibilité de la modifier et de la stocker.  
  
 La classe <xref:System.Threading.Interlocked> fournit les opérations suivantes :  
  
-   La méthode <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> ajoute une valeur entière à une variable et retourne la nouvelle valeur de la variable.  
  
-   La méthode <xref:System.Threading.Interlocked.Read%2A?displayProperty=nameWithType> lit une valeur entière 64 bits sous forme d’opération atomique. Cela est utile sur les systèmes d’exploitation 32 bits, où la lecture d’un entier 64 bits n’est en général pas une opération atomique.  
  
-   Les méthodes <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> et <xref:System.Threading.Interlocked.Decrement%2A?displayProperty=nameWithType> incrémentent ou décrémentent une variable et retournent la valeur résultante.  
  
-   La méthode <xref:System.Threading.Interlocked.Exchange%2A?displayProperty=nameWithType> exécute un échange atomique de la valeur dans une variable spécifiée, en renvoyant la valeur et en la remplaçant par une nouvelle valeur. Utilisez une surcharge <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29> générique de cette méthode pour exécuter l’échange sur une variable de tout type de référence.  
  
-   La méthode <xref:System.Threading.Interlocked.CompareExchange%2A?displayProperty=nameWithType> échange également deux valeurs, mais dépend du résultat d’une comparaison. Utilisez une surcharge <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> générique de cette méthode pour exécuter l’échange sur une variable de tout type de référence.  
  
 Sur les processeurs modernes, les méthodes de la classe <xref:System.Threading.Interlocked> peuvent souvent être implémentées par une seule instruction. Par conséquent, elles fournissent d’excellentes performances de synchronisation et peuvent être utilisées pour générer des mécanismes de synchronisation de niveau supérieur, comme des verrous de rotation.  
  
 Pour obtenir un exemple utilisant une combinaison des classes <xref:System.Threading.Monitor> et <xref:System.Threading.Interlocked>, consultez [Moniteurs](https://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
## <a name="compareexchange-example"></a>Exemple CompareExchange

 La méthode <xref:System.Threading.Interlocked.CompareExchange%2A> peut être utilisée pour protéger des calculs qui sont plus compliqués que de simples incréments et décréments. L’exemple suivant montre une méthode thread-safe qui s’ajoute à un total d’exécution stocké comme nombre à virgule flottante. (Pour les entiers, la méthode <xref:System.Threading.Interlocked.Add%2A> est une solution plus simple.) Pour des exemples de code complet, consultez les surcharges de <xref:System.Threading.Interlocked.CompareExchange%2A> qui acceptent les arguments à virgule flottante simple précision et double précision (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> et <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a>Surcharges non typées d’Exchange et de CompareExchange

 Les méthodes <xref:System.Threading.Interlocked.Exchange%2A> et <xref:System.Threading.Interlocked.CompareExchange%2A> ont des surcharges qui acceptent les arguments de type <xref:System.Object>. Le premier argument de chacune de ces surcharges est `ref Object` (`ByRef … As Object` dans Visual Basic), et la cohérence des types nécessite que la variable transmise à cet argument soit typée de manière stricte comme <xref:System.Object>. Il ne suffit pas de caster le premier argument sur le type <xref:System.Object> quand vous appelez ces méthodes.  
  
> [!NOTE]
>  Dans .NET Framework version 2.0 et versions ultérieures, utilisez les surcharges génériques des méthodes <xref:System.Threading.Interlocked.Exchange%2A> et <xref:System.Threading.Interlocked.CompareExchange%2A> pour échanger des variables fortement typées.  
  
 L’exemple de code suivant montre une propriété de type `ClassA` qui peut être définie une seule fois, dans la mesure où elle pourrait être implémentée dans .NET Framework version 1.0 ou 1.1.  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Interlocked?displayProperty=nameWithType>  
- <xref:System.Threading.Monitor?displayProperty=nameWithType>  
- [Thread](index.md)  
- [Fonctionnalités et objets de threading](threading-objects-and-features.md)
