---
title: Traiter les tâches asynchrones terminées
ms.date: 09/12/2018
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: 5ce677a791427e7e064a2c12a9e09aba34a67560
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45617180"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a>Démarrer plusieurs tâches Async et les traiter une fois terminées (C#)

En utilisant <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, vous pouvez démarrer plusieurs tâches en même temps et les traiter une par une, une fois qu’elles sont terminées, au lieu de les traiter dans l’ordre dans lequel elles ont démarré.

L’exemple suivant utilise une requête pour créer une collection de tâches. Chaque tâche télécharge le contenu d’un site web spécifié. À chaque itération d’une boucle while, un appel attendu à `WhenAny` retourne la tâche de la collection de tâches dont le téléchargement se termine en premier. Cette tâche est supprimée de la collection et traitée. La boucle se répète jusqu’à ce que la collection ne contienne plus aucune tâche.

> [!NOTE]
> Pour exécuter les exemples, Visual Studio 2012 ou version ultérieure et .NET Framework 4.5 ou version ultérieure doivent être installés sur votre ordinateur.

## <a name="download-an-example-solution"></a>Télécharger un exemple de solution

Téléchargez l’intégralité du projet Windows Presentation Foundation (WPF) à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea), puis procédez comme suit.

> [!TIP]
> Si vous ne souhaitez pas télécharger le projet, vous pouvez passer en revue le fichier MainWindow.xaml.cs à la fin de cette rubrique à la place.

1.  Extrayez les fichiers que vous avez téléchargés à partir du fichier .zip, puis démarrez Visual Studio.

2.  Dans la barre de menus, choisissez **Fichier** > **Ouvrir** > **Projet/Solution**.

3.  Dans la boîte de dialogue **Ouvrir le projet**, ouvrez le dossier contenant l’exemple de code que vous avez téléchargé, puis ouvrez le fichier de solution (.sln) pour AsyncFineTuningCS.

4.  Dans l’**Explorateur de solutions**, ouvrez le menu contextuel pour le projet **ProcessTasksAsTheyFinish**, puis choisissez **Définir comme projet de démarrage**.

5.  Choisissez la touche **F5** pour exécuter le programme (ou appuyez sur **Ctrl**+**F5** pour exécuter le programme sans le déboguer).

6.  Exécutez le projet plusieurs fois pour vérifier que les longueurs téléchargées n’apparaissent pas toujours dans le même ordre.

## <a name="create-the-program-yourself"></a>Créer le programme vous-même

Cet exemple ajoute le code développé dans [Annuler les tâches Async restantes lorsque l’une d’elles est terminée (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) et utilise la même interface utilisateur.

Pour générer l’exemple vous-même, pas à pas, suivez les instructions de la section [Téléchargement de l’exemple](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example), mais choisissez **CancelAfterOneTask** comme projet de démarrage. Ajoutez les modifications de cette rubrique à la méthode `AccessTheWebAsync` dans ce projet. Les modifications sont marquées par des astérisques.

Le projet **CancelAfterOneTask** inclut déjà une requête qui, lorsqu’elle est exécutée, crée une collection de tâches. Chaque appel à `ProcessURLAsync` dans le code suivant retourne un <xref:System.Threading.Tasks.Task%601>, où `TResult` est un entier :

```csharp
IEnumerable<Task<int>> downloadTasksQuery = from url in urlList select ProcessURL(url, client, ct);
```

Dans le fichier MainWindow.xaml.cs du projet, apportez les modifications suivantes à la méthode `AccessTheWebAsync`.

-   Exécutez la requête en appliquant <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> au lieu de <xref:System.Linq.Enumerable.ToArray%2A>.

    ```csharp
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
    ```

-   Ajoutez une boucle `while` qui effectue les étapes suivantes pour chaque tâche dans la collection :

    1.  Elle attend un appel à `WhenAny` pour identifier la première tâche dans la collection afin de terminer son téléchargement.

        ```csharp
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
        ```

    2.  Elle supprime cette tâche de la collection.

        ```csharp
        downloadTasks.Remove(firstFinishedTask);
        ```

    3.  Elle attend `firstFinishedTask`, qui est retourné par un appel à `ProcessURLAsync`. La variable `firstFinishedTask` est un <xref:System.Threading.Tasks.Task%601> où `TReturn` est un entier. La tâche est déjà terminée, mais vous l’attendez pour récupérer la longueur du site web téléchargé, comme le montre l’exemple suivant.

        ```csharp
        int length = await firstFinishedTask;
        resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);
        ```

Exécutez le programme plusieurs fois pour vérifier que les longueurs téléchargées n’apparaissent pas toujours dans le même ordre.

> [!CAUTION]
> Vous pouvez utiliser `WhenAny` dans une boucle, comme décrit dans l’exemple, pour résoudre les problèmes qui impliquent un petit nombre de tâches. Cependant, d’autres approches sont plus efficaces si vous avez un grand nombre de tâches à traiter. Pour plus d’informations et d’exemples, consultez [Traitement des tâches une fois terminées](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/).

## <a name="complete-example"></a>Exemple complet

Le code suivant est le texte complet du fichier MainWindow.xaml.cs de l’exemple. Des astérisques marquent les éléments ajoutés pour cet exemple. Notez aussi que vous devez ajouter une référence pour <xref:System.Net.Http>.

Vous pouvez télécharger le projet à partir de la page [Exemple Async : réglage de votre application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;

// Add a using directive and a reference for System.Net.Http.
using System.Net.Http;

// Add the following using directive.
using System.Threading;

namespace ProcessTasksAsTheyFinish
{
    public partial class MainWindow : Window
    {
        // Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            resultsTextBox.Clear();

            // Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            try
            {
                await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text += "\r\nDownloads complete.";
            }
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownloads canceled.\r\n";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownloads failed.\r\n";
            }

            cts = null;
        }

        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        async Task AccessTheWebAsync(CancellationToken ct)
        {
            HttpClient client = new HttpClient();

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // ***Create a query that, when executed, returns a collection of tasks.
            IEnumerable<Task<int>> downloadTasksQuery =
                from url in urlList select ProcessURL(url, client, ct);

            // ***Use ToList to execute the query and start the tasks.
            List<Task<int>> downloadTasks = downloadTasksQuery.ToList();

            // ***Add a loop to process the tasks one at a time until none remain.
            while (downloadTasks.Count > 0)
            {
                    // Identify the first task that completes.
                    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);

                    // ***Remove the selected task from the list so that you don't
                    // process it more than once.
                    downloadTasks.Remove(firstFinishedTask);

                    // Await the completed task.
                    int length = await firstFinishedTask;
                    resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "http://msdn.microsoft.com",
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "http://msdn.microsoft.com/library/hh290136.aspx",
                "http://msdn.microsoft.com/library/dd470362.aspx",
                "http://msdn.microsoft.com/library/aa578028.aspx",
                "http://msdn.microsoft.com/library/ms404677.aspx",
                "http://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        async Task<int> ProcessURL(string url, HttpClient client, CancellationToken ct)
        {
            // GetAsync returns a Task<HttpResponseMessage>.
            HttpResponseMessage response = await client.GetAsync(url, ct);

            // Retrieve the website contents from the HttpResponseMessage.
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

            return urlContents.Length;
        }
    }
}

// Sample Output:

// Length of the download:  226093
// Length of the download:  412588
// Length of the download:  175490
// Length of the download:  204890
// Length of the download:  158855
// Length of the download:  145790
// Length of the download:  44908
// Downloads complete.
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Ajuster une application Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Programmation asynchrone avec Async et Await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [Exemple Async : ajuster une application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)