---
title: Guide pratique pour rechercher des attributs de frères avec un nom spécifique (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: c3133d64-523f-422d-8838-73d36b945ca0
ms.openlocfilehash: 60b6529f310ccbb02160ff96e1db7870bcc71058
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863119"
---
# <a name="how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml-c"></a>Guide pratique pour rechercher des attributs de frères avec un nom spécifique (XPath-LINQ to XML) (C#)
Cette rubrique montre comment rechercher tous les attributs des frères du nœud de contexte. Seuls les attributs avec un nom spécifique sont retournés dans la collection.  
  
 L’expression XPath est la suivante :  
  
 `../Book/@id`  
  
## <a name="example"></a>Exemple  
 Cet exemple recherche d'abord un élément `Book`, puis tous les éléments frères nommés `Book`, puis tous les attributs nommés `id`. Le résultat est une collection d’attributs.  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Livres (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
```csharp  
XDocument books = XDocument.Load("Books.xml");  
  
XElement book =   
    books  
    .Root  
    .Element("Book");  
  
// LINQ to XML query  
IEnumerable<XAttribute> list1 =  
    from el in book.Parent.Elements("Book")  
    select el.Attribute("id");  
  
// XPath expression  
IEnumerable<XAttribute> list2 =  
  ((IEnumerable)book.XPathEvaluate("../Book/@id")).Cast<XAttribute>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XAttribute el in list1)  
    Console.WriteLine(el);  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
Results are identical  
id="bk101"  
id="bk102"  
```  
  
## <a name="see-also"></a>Voir aussi

- [LINQ to XML pour les utilisateurs XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
