---
title: Indications pour la mise en forme du code (F#)
description: "Découvrez les instructions de mise en forme de mise en retrait code pour le langage de programmation pour une meilleure lisibilité, esthétique, la normalisation et la compilation F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3f79717c-f84e-448d-9ce4-90e40a644ba1
ms.openlocfilehash: cc56c67f356b99defd8dc28770f87be1f58443c5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="code-formatting-guidelines"></a><span data-ttu-id="a2056-104">Indications pour la mise en forme du code</span><span class="sxs-lookup"><span data-stu-id="a2056-104">Code Formatting Guidelines</span></span>

<span data-ttu-id="a2056-105">Cette rubrique résume les instructions de mise en retrait de code pour F #.</span><span class="sxs-lookup"><span data-stu-id="a2056-105">This topic summarizes code indentation guidelines for F#.</span></span> <span data-ttu-id="a2056-106">Étant donné que le langage F # est sensible aux sauts de ligne et de mise en retrait, il n’est pas simplement une question de lisibilité, esthétique ou le codage normalisation problème pour mettre correctement en forme votre code.</span><span class="sxs-lookup"><span data-stu-id="a2056-106">Because the F# language is sensitive to line breaks and indentation, it is not just a readability issue, aesthetic issue, or coding standardization issue to format your code correctly.</span></span> <span data-ttu-id="a2056-107">Vous devez mettre en forme votre code correctement pour qu’il se compile correctement.</span><span class="sxs-lookup"><span data-stu-id="a2056-107">You must format your code correctly for it to compile correctly.</span></span>


## <a name="general-rules-for-indentation"></a><span data-ttu-id="a2056-108">Règles générales pour la mise en retrait</span><span class="sxs-lookup"><span data-stu-id="a2056-108">General Rules for Indentation</span></span>
<span data-ttu-id="a2056-109">Lors de la mise en retrait est requise, vous devez utiliser des espaces, tabulations pas.</span><span class="sxs-lookup"><span data-stu-id="a2056-109">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="a2056-110">Au moins un espace est requis.</span><span class="sxs-lookup"><span data-stu-id="a2056-110">At least one space is required.</span></span> <span data-ttu-id="a2056-111">Votre organisation peut créer des normes de codage pour spécifier le nombre d’espaces à utiliser pour la mise en retrait ; trois ou quatre espaces de mise en retrait à chaque niveau de mise en retrait est typique.</span><span class="sxs-lookup"><span data-stu-id="a2056-111">Your organization can create coding standards to specify the number of spaces to use for indentation; three or four spaces of indentation at each level where indentation occurs is typical.</span></span> <span data-ttu-id="a2056-112">Vous pouvez configurer Visual Studio en fonction des normes de mise en retrait de votre organisation en modifiant les options de la `Options` boîte de dialogue, qui est disponible à partir de la `Tools` menu.</span><span class="sxs-lookup"><span data-stu-id="a2056-112">You can configure Visual Studio to match your organization's indentation standards by changing the options in the `Options` dialog box, which is available from the `Tools` menu.</span></span> <span data-ttu-id="a2056-113">Dans le `Text Editor` nœud, développez `F#` puis cliquez sur `Tabs`.</span><span class="sxs-lookup"><span data-stu-id="a2056-113">In the `Text Editor` node, expand `F#` and then click `Tabs`.</span></span> <span data-ttu-id="a2056-114">Pour obtenir une description des options disponibles, consultez [Options, éditeur de texte, tous les langages, onglets](https://msdn.microsoft.com/library/7sffa753.aspx).</span><span class="sxs-lookup"><span data-stu-id="a2056-114">For a description of the available options, see [Options, Text Editor, All Languages, Tabs](https://msdn.microsoft.com/library/7sffa753.aspx).</span></span>

<span data-ttu-id="a2056-115">En règle générale, lorsque le compilateur analyse votre code, il conserve une pile interne qui indique le niveau d’imbrication actuel.</span><span class="sxs-lookup"><span data-stu-id="a2056-115">In general, when the compiler parses your code, it maintains an internal stack that indicates the current level of nesting.</span></span> <span data-ttu-id="a2056-116">Lorsque le code est mis en retrait, un nouveau niveau d’imbrication est créé, ou cette pile interne.</span><span class="sxs-lookup"><span data-stu-id="a2056-116">When code is indented, a new level of nesting is created, or pushed onto this internal stack.</span></span> <span data-ttu-id="a2056-117">Lorsqu’une construction se termine, le niveau est dépilé.</span><span class="sxs-lookup"><span data-stu-id="a2056-117">When a construct ends, the level is popped.</span></span> <span data-ttu-id="a2056-118">Mise en retrait est un moyen pour signaler la fin d’un niveau et de dépiler la pile interne, mais certains jetons provoquent également le niveau d’être dépilés, telles que le `end` (mot clé), ou d’une accolade fermante ou une parenthèse.</span><span class="sxs-lookup"><span data-stu-id="a2056-118">Indentation is one way to signal the end of a level and pop the internal stack, but certain tokens also cause the level to be popped, such as the `end` keyword, or a closing brace or parenthesis.</span></span>

<span data-ttu-id="a2056-119">Le code dans une construction multiligne, comme une définition de type, définition de fonction, `try...with` construction et constructions de bouclage, doivent être mis en retrait par rapport à la ligne d’ouverture de la construction.</span><span class="sxs-lookup"><span data-stu-id="a2056-119">Code in a multiline construct, such as a type definition, function definition, `try...with` construct, and looping constructs, must be indented relative to the opening line of the construct.</span></span> <span data-ttu-id="a2056-120">La première ligne mise en retrait établit une position de colonne pour le code suivant dans la même construction.</span><span class="sxs-lookup"><span data-stu-id="a2056-120">The first indented line establishes a column position for subsequent code in the same construct.</span></span> <span data-ttu-id="a2056-121">Le niveau de mise en retrait est appelé un *contexte*.</span><span class="sxs-lookup"><span data-stu-id="a2056-121">The indentation level is called a *context*.</span></span> <span data-ttu-id="a2056-122">La position de colonne définit une colonne minimale, appelée un *ligne hors-jeu*, pour les lignes de code qui se trouvent dans le même contexte.</span><span class="sxs-lookup"><span data-stu-id="a2056-122">The column position sets a minimum column, referred to as an *offside line*, for subsequent lines of code that are in the same context.</span></span> <span data-ttu-id="a2056-123">Lorsqu’une ligne de code est rencontrée, qui est mis en retrait inférieure à la position de colonne établie, le compilateur suppose que le contexte est terminée et que vous codez maintenant au niveau suivant, dans le contexte précédent.</span><span class="sxs-lookup"><span data-stu-id="a2056-123">When a line of code is encountered that is indented less than this established column position, the compiler assumes that the context has ended and that you are now coding at the next level up, in the previous context.</span></span> <span data-ttu-id="a2056-124">Le terme *hors-jeu* est utilisé pour décrire la condition dans laquelle une ligne de code déclenche la fin d’une construction, car elle n’est pas suffisamment mise en retrait.</span><span class="sxs-lookup"><span data-stu-id="a2056-124">The term *offside* is used to describe the condition in which a line of code triggers the end of a construct because it is not indented far enough.</span></span> <span data-ttu-id="a2056-125">En d’autres termes, le code à gauche d’une ligne hors-jeu est hors-jeu.</span><span class="sxs-lookup"><span data-stu-id="a2056-125">In other words, code to the left of an offside line is offside.</span></span> <span data-ttu-id="a2056-126">Dans le code mis en retrait correctement, vous tirer parti de la règle de hors-jeu afin de définir la fin de constructions.</span><span class="sxs-lookup"><span data-stu-id="a2056-126">In correctly indented code, you take advantage of the offside rule in order to delineate the end of constructs.</span></span> <span data-ttu-id="a2056-127">Si vous utilisez incorrectement mise en retrait, une condition de hors-jeu peut contraindre le compilateur à émettre un avertissement ou peut provoquer l’interprétation incorrecte de votre code.</span><span class="sxs-lookup"><span data-stu-id="a2056-127">If you use indentation improperly, an offside condition can cause the compiler to issue a warning or can lead to the incorrect interpretation of your code.</span></span>

<span data-ttu-id="a2056-128">Lignes hors-jeu sont déterminées comme suit.</span><span class="sxs-lookup"><span data-stu-id="a2056-128">Offside lines are determined as follows.</span></span>


- <span data-ttu-id="a2056-129">Un `=` jeton associé à un `let` introduit une ligne hors-jeu au niveau de la colonne du premier jeton après le `=` signe.</span><span class="sxs-lookup"><span data-stu-id="a2056-129">An `=` token associated with a `let` introduces an offside line at the column of the first token after the `=` sign.</span></span>


- <span data-ttu-id="a2056-130">Dans un `if...then...else` expression, la position de colonne du premier jeton après le `then` mot clé ou le `else` mot clé introduit une ligne hors-jeu.</span><span class="sxs-lookup"><span data-stu-id="a2056-130">In an `if...then...else` expression, the column position of the first token after the `then` keyword or the `else` keyword introduces an offside line.</span></span>


- <span data-ttu-id="a2056-131">Dans un `try...with` expression, le premier jeton après `try` introduit une ligne hors-jeu.</span><span class="sxs-lookup"><span data-stu-id="a2056-131">In a `try...with` expression, the first token after `try` introduces an offside line.</span></span>


- <span data-ttu-id="a2056-132">Dans un `match` expression, le premier jeton après `with` et le premier jeton après chaque `->` introduisent des lignes hors-jeu.</span><span class="sxs-lookup"><span data-stu-id="a2056-132">In a `match` expression, the first token after `with` and the first token after each `->` introduce offside lines.</span></span>


- <span data-ttu-id="a2056-133">Le premier jeton après `with` dans un type d’extension introduit une ligne hors-jeu.</span><span class="sxs-lookup"><span data-stu-id="a2056-133">The first token after `with` in a type extension introduces an offside line.</span></span>


- <span data-ttu-id="a2056-134">Le premier jeton après une accolade ouvrante ou une parenthèse, ou après le `begin` (mot clé), introduit une ligne hors-jeu.</span><span class="sxs-lookup"><span data-stu-id="a2056-134">The first token after an opening brace or parenthesis, or after the `begin` keyword, introduces an offside line.</span></span>


- <span data-ttu-id="a2056-135">Le premier caractère dans les mots clés `let`, `if`, et `module` introduisent des lignes hors-jeu.</span><span class="sxs-lookup"><span data-stu-id="a2056-135">The first character in the keywords `let`, `if`, and `module` introduce offside lines.</span></span>


<span data-ttu-id="a2056-136">Les exemples de code suivants illustrent les règles de mise en retrait.</span><span class="sxs-lookup"><span data-stu-id="a2056-136">The following code examples illustrate the indentation rules.</span></span> <span data-ttu-id="a2056-137">Ici, les instructions print s’appuient sur la mise en retrait pour les associer avec le contexte approprié.</span><span class="sxs-lookup"><span data-stu-id="a2056-137">Here, the print statements rely on indentation to associate them with the appropriate context.</span></span> <span data-ttu-id="a2056-138">Chaque fois que la mise en retrait est décalé vers, le contexte est dépilé et retourne au contexte précédent.</span><span class="sxs-lookup"><span data-stu-id="a2056-138">Every time the indentation shifts, the context is popped and returns to the previous context.</span></span> <span data-ttu-id="a2056-139">Par conséquent, un espace est imprimé à la fin de chaque itération ; « Terminé » !</span><span class="sxs-lookup"><span data-stu-id="a2056-139">Therefore, a space is printed at the end of each iteration; "Done!"</span></span> <span data-ttu-id="a2056-140">est imprimé uniquement une seule fois, car la mise en retrait hors-jeu établit qu’il n’est pas partie de la boucle.</span><span class="sxs-lookup"><span data-stu-id="a2056-140">is only printed one time because the offside indentation establishes that it is not part of the loop.</span></span> <span data-ttu-id="a2056-141">L’impression de la chaîne « Contexte de niveau supérieur » ne fait pas partie de la fonction.</span><span class="sxs-lookup"><span data-stu-id="a2056-141">The printing of the string "Top-level context" is not part of the function.</span></span> <span data-ttu-id="a2056-142">Par conséquent, il est imprimé en premier lieu, pendant l’initialisation statique, avant que la fonction est appelée.</span><span class="sxs-lookup"><span data-stu-id="a2056-142">Therefore, it is printed first, during the static initialization, before the function is called.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet1.fs)]

<span data-ttu-id="a2056-143">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="a2056-143">The output is as follows.</span></span>

```
Top-level context

(Negative number) Zero 1 2 3 Done!
```

<span data-ttu-id="a2056-144">Lorsque vous vous arrêtez les longues lignes, la continuation de la ligne doit être plus en retrait la construction englobante.</span><span class="sxs-lookup"><span data-stu-id="a2056-144">When you break long lines, the continuation of the line must be indented farther than the enclosing construct.</span></span> <span data-ttu-id="a2056-145">Par exemple, les arguments de fonction doivent être plus en retrait le premier caractère du nom de fonction, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="a2056-145">For example, function arguments must be indented farther than the first character of the function name, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet2.fs)]

<span data-ttu-id="a2056-146">Il existe des exceptions à ces règles, comme décrit dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="a2056-146">There are exceptions to these rules, as described in the next section.</span></span>


## <a name="indentation-in-modules"></a><span data-ttu-id="a2056-147">Mise en retrait dans les Modules</span><span class="sxs-lookup"><span data-stu-id="a2056-147">Indentation in Modules</span></span>
<span data-ttu-id="a2056-148">Code dans un module local doit être mis en retrait par rapport au module, mais le code dans un module de niveau supérieur ne doit pas être mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="a2056-148">Code in a local module must be indented relative to the module, but code in a top-level module does not have to be indented.</span></span> <span data-ttu-id="a2056-149">Les éléments Namespace n’ont pas à être mis en retrait.</span><span class="sxs-lookup"><span data-stu-id="a2056-149">Namespace elements do not have to be indented.</span></span>

<span data-ttu-id="a2056-150">Les exemples de code suivants illustrent ce principe.</span><span class="sxs-lookup"><span data-stu-id="a2056-150">The following code examples illustrate this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet3.fs)]
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet4.fs)]

<span data-ttu-id="a2056-151">Pour plus d’informations, consultez [Modules](modules.md).</span><span class="sxs-lookup"><span data-stu-id="a2056-151">For more information, see [Modules](modules.md).</span></span>


## <a name="exceptions-to-the-basic-indentation-rules"></a><span data-ttu-id="a2056-152">Exceptions aux règles de mise en retrait de base</span><span class="sxs-lookup"><span data-stu-id="a2056-152">Exceptions to the Basic Indentation Rules</span></span>
<span data-ttu-id="a2056-153">La règle générale, comme décrit dans la section précédente, est que code dans les constructions multilignes doit être mis en retrait par rapport à la mise en retrait de la première ligne de la construction, et que la fin de la construction est déterminée par lors de la première ligne hors-jeu se produit.</span><span class="sxs-lookup"><span data-stu-id="a2056-153">The general rule, as described in the previous section, is that code in multiline constructs must be indented relative to the indentation of the first line of the construct, and that the end of the construct is determined by when the first offside line occurs.</span></span> <span data-ttu-id="a2056-154">Une exception à la règle lorsque la fin de contextes est que certaines constructions, telles que la `try...with` expression, le `if...then...else` expression et l’utilisation de `and` syntaxe de déclaration mutuellement les fonctions récursives ou types, de plusieurs parties.</span><span class="sxs-lookup"><span data-stu-id="a2056-154">An exception to the rule about when contexts end is that some constructs, such as the `try...with` expression, the `if...then...else` expression, and the use of `and` syntax for declaring mutually recursive functions or types, have multiple parts.</span></span> <span data-ttu-id="a2056-155">Vous mettez en retrait les dernières parties, telles que `then` et `else` dans un `if...then...else` expression, au même niveau que le jeton qui démarre l’expression, mais au lieu d’indiquer une fin au contexte, il représente la partie suivante du même contexte.</span><span class="sxs-lookup"><span data-stu-id="a2056-155">You indent the later parts, such as `then` and `else` in an `if...then...else` expression, at the same level as the token that starts the expression, but instead of indicating an end to the context, it represents the next part of the same context.</span></span> <span data-ttu-id="a2056-156">Par conséquent, un `if...then...else` expression peut être écrite comme dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="a2056-156">Therefore, an `if...then...else` expression can be written as in the following code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet5.fs)]

<span data-ttu-id="a2056-157">L’exception à la règle de hors-jeu s’applique uniquement à la `then` et `else` mots clés.</span><span class="sxs-lookup"><span data-stu-id="a2056-157">The exception to the offside rule applies only to the `then` and `else` keywords.</span></span> <span data-ttu-id="a2056-158">Par conséquent, même s’il n’est pas une erreur pour mettre en retrait le `then` et `else` davantage, ne peut pas mettre en retrait les lignes de code dans un `then` bloc génère un avertissement.</span><span class="sxs-lookup"><span data-stu-id="a2056-158">Therefore, although it is not an error to indent the `then` and `else` further, failing to indent the lines of code in a `then` block produces a warning.</span></span> <span data-ttu-id="a2056-159">Ceci est illustré dans les lignes de code suivantes.</span><span class="sxs-lookup"><span data-stu-id="a2056-159">This is illustrated in the following lines of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet6.fs)]
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet7.fs)]

<span data-ttu-id="a2056-160">Pour le code dans un `else` bloc, une règle spéciale supplémentaire s’applique.</span><span class="sxs-lookup"><span data-stu-id="a2056-160">For code in an `else` block, an additional special rule applies.</span></span> <span data-ttu-id="a2056-161">L’avertissement dans l’exemple précédent se produit uniquement sur le code dans le `then` blocs, pas sur le code dans le `else` bloc.</span><span class="sxs-lookup"><span data-stu-id="a2056-161">The warning in the previous example occurs only on the code in the `then` block, not on the code in the `else` block.</span></span> <span data-ttu-id="a2056-162">Cela vous permet d’écrire du code qui vérifie différentes conditions au début d’une fonction sans forcer le reste du code pour la fonction, ce qui peut être dans un `else` bloc, d’être mises en retrait.</span><span class="sxs-lookup"><span data-stu-id="a2056-162">This allows you to write code that checks for various conditions at the beginning of a function without forcing the rest of the code for the function, which might be in an `else` block, to be indented.</span></span> <span data-ttu-id="a2056-163">Par conséquent, vous pouvez écrire ce qui suit sans générer d’avertissement.</span><span class="sxs-lookup"><span data-stu-id="a2056-163">Thus, you can write the following without producing a warning.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet8.fs)]

<span data-ttu-id="a2056-164">Une autre exception à la règle de contextes se terminent lorsqu’une ligne n’est pas mise en retrait comme une ligne précédente est tel que pour les opérateurs infix `+` et `|>`.</span><span class="sxs-lookup"><span data-stu-id="a2056-164">Another exception to the rule that contexts end when a line is not indented as far as a previous line is for infix operators, such as `+` and `|>`.</span></span> <span data-ttu-id="a2056-165">Les lignes qui commencent par les opérateurs infixes sont autorisées à commencer `(1 + oplength)` colonnes avant la position normale, sans déclencher la fin du contexte, où `oplength` est le nombre de caractères qui composent l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="a2056-165">Lines that start with infix operators are permitted to begin `(1 + oplength)` columns before the normal position without triggering an end to the context, where `oplength` is the number of characters that make up the operator.</span></span> <span data-ttu-id="a2056-166">Ainsi, le premier jeton après l’opérateur pour les aligner avec la ligne précédente.</span><span class="sxs-lookup"><span data-stu-id="a2056-166">This causes the first token after the operator to align with the previous line.</span></span>

<span data-ttu-id="a2056-167">Par exemple, dans le code suivant, le `+` symbole est autorisé à être mis en retrait de deux colonnes inférieur à la ligne précédente.</span><span class="sxs-lookup"><span data-stu-id="a2056-167">For example, in the following code, the `+` symbol is permitted to be indented two columns less than the previous line.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet9.fs)]

<span data-ttu-id="a2056-168">Bien que la mise en retrait augmente généralement à mesure que le niveau d’imbrication supérieur, il existe plusieurs constructions dans lequel le compilateur vous permet de réinitialiser la mise en retrait à une position de colonne inférieure.</span><span class="sxs-lookup"><span data-stu-id="a2056-168">Although indentation usually increases as the level of nesting becomes higher, there are several constructs in which the compiler allows you to reset the indentation to a lower column position.</span></span>

<span data-ttu-id="a2056-169">Les constructions qui autorisent une réinitialisation de position de colonne sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a2056-169">The constructs that permit a reset of column position are as follows:</span></span>


- <span data-ttu-id="a2056-170">Corps de fonctions anonymes.</span><span class="sxs-lookup"><span data-stu-id="a2056-170">Bodies of anonymous functions.</span></span> <span data-ttu-id="a2056-171">Dans le code suivant, l’expression print commence à une position de colonne qui est plue à gauche que le `fun` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="a2056-171">In the following code, the print expression starts at a column position that is farther to the left than the `fun` keyword.</span></span> <span data-ttu-id="a2056-172">Toutefois, la ligne ne doit pas commencer à une colonne à gauche du début du niveau de mise en retrait précédent (autrement dit, à gauche de la `L` dans `List`).</span><span class="sxs-lookup"><span data-stu-id="a2056-172">However, the line must not start at a column to the left of the start of the previous indentation level (that is, to the left of the `L` in `List`).</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet10.fs)]

- <span data-ttu-id="a2056-173">Constructions entre parenthèses ou entre `begin` et `end` dans un `then` ou `else` bloquer d’un `if...then...else` fourni d’expression, la mise en retrait n’est pas inférieure à la position de colonne de la `if` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="a2056-173">Constructs enclosed by parentheses or by `begin` and `end` in a `then` or `else` block of an `if...then...else` expression, provided the indentation is no less than the column position of the `if` keyword.</span></span> <span data-ttu-id="a2056-174">Cette exception autorise un style de programmation dans lequel une parenthèse ouvrante ou `begin` est utilisé à la fin d’une ligne après `then` ou `else`.</span><span class="sxs-lookup"><span data-stu-id="a2056-174">This exception allows for a coding style in which an opening parenthesis or `begin` is used at the end of a line after `then` or `else`.</span></span>


- <span data-ttu-id="a2056-175">Corps des modules, des classes, des interfaces et des structures délimités par `begin...end`, `{...}`, `class...end`, ou `interface...end`.</span><span class="sxs-lookup"><span data-stu-id="a2056-175">Bodies of modules, classes, interfaces, and structures delimited by `begin...end`, `{...}`, `class...end`, or `interface...end`.</span></span> <span data-ttu-id="a2056-176">Cela permet à un style dans lequel le mot clé d’ouverture d’une définition de type peut être sur la même ligne que le nom de type sans forcer le corps entier à être mis en retrait soulevez-la le mot clé d’ouverture.</span><span class="sxs-lookup"><span data-stu-id="a2056-176">This allows for a style in which the opening keyword of a type definition can be on the same line as the type name without forcing the whole body to be indented farther than the opening keyword.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet13.fs)]


## <a name="see-also"></a><span data-ttu-id="a2056-177">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2056-177">See Also</span></span>
[<span data-ttu-id="a2056-178">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="a2056-178">F# Language Reference</span></span>](index.md)