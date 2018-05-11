### <a name="icommandcanexecutechanged-event-behaviour-changed-in-net-45"></a><span data-ttu-id="f72ec-101">Le comportement de l’événement ICommand.CanExecuteChanged a changé dans .NET 4.5</span><span class="sxs-lookup"><span data-stu-id="f72ec-101">ICommand.CanExecuteChanged event behaviour changed in .NET 4.5</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f72ec-102">Détails</span><span class="sxs-lookup"><span data-stu-id="f72ec-102">Details</span></span>|<span data-ttu-id="f72ec-103">Dans .NET Framework 4.5, <xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=name> était ignoré, sauf si l’objet qui avait envoyé l’événement était le même que celui qui l’avait déclenché.</span><span class="sxs-lookup"><span data-stu-id="f72ec-103">In the .NET Framework 4.5, a <xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=name> was ignored unless the sender of the event was the same object as the object that raised the event.</span></span> <span data-ttu-id="f72ec-104">Ce bogue a été corrigé dans les mises à jour de maintenance de .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="f72ec-104">This bug was fixed in .NET Framework 4.5 servicing updates.</span></span>|
|<span data-ttu-id="f72ec-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="f72ec-105">Suggestion</span></span>|<span data-ttu-id="f72ec-106">Ce bogue a été résolu dans les versions de maintenance du .NET Framework 4.5. Vous pouvez donc l’éviter en vérifiant que votre .NET Framework est à jour ou en le mettant à niveau vers .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="f72ec-106">This bug has been fixed in the .NET Framework 4.5 servicing releases, so it can be avoided by making sure that the .NET Framework is up-to-date or by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="f72ec-107">Vous pouvez également modifier le code d’application <xref:System.Windows.Input.ICommand?displayProperty=name> pour veiller à ce que lorsqu’il déclenche une commande <xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=name>, l’objet qui envoie l’événement soit le même que celui qui déclenche l’événement.</span><span class="sxs-lookup"><span data-stu-id="f72ec-107">Alternatively, application code using <xref:System.Windows.Input.ICommand?displayProperty=name> can be modified to make sure that the sender when raising a <xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=name> command is the same as the object raising the event.</span></span>|
|<span data-ttu-id="f72ec-108">Portée</span><span class="sxs-lookup"><span data-stu-id="f72ec-108">Scope</span></span>|<span data-ttu-id="f72ec-109">Mineur</span><span class="sxs-lookup"><span data-stu-id="f72ec-109">Minor</span></span>|
|<span data-ttu-id="f72ec-110">Version</span><span class="sxs-lookup"><span data-stu-id="f72ec-110">Version</span></span>|<span data-ttu-id="f72ec-111">4.5</span><span class="sxs-lookup"><span data-stu-id="f72ec-111">4.5</span></span>|
|<span data-ttu-id="f72ec-112">Type</span><span class="sxs-lookup"><span data-stu-id="f72ec-112">Type</span></span>|<span data-ttu-id="f72ec-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="f72ec-113">Runtime</span></span>|
|<span data-ttu-id="f72ec-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="f72ec-114">Affected APIs</span></span>|<ul><li><xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=nameWithType></li></ul>|
|<span data-ttu-id="f72ec-115">Analyseurs</span><span class="sxs-lookup"><span data-stu-id="f72ec-115">Analyzers</span></span>|<ul><li><span data-ttu-id="f72ec-116">CD0084</span><span class="sxs-lookup"><span data-stu-id="f72ec-116">CD0084</span></span></li></ul>|
