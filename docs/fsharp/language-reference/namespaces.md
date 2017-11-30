---
title: "命名空间 (F#)"
description: "了解如何使用 F # 命名空间，可将代码组织到相关的功能区域，通过使你能够将名称附加到的程序元素分组。"
keywords: "visual f#, f#, 函数编程"
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea42156f-e1b9-4535-9383-b45f46f3f7ca
ms.openlocfilehash: 4378afebe6fd0d9317f734457576dc75d7488bf0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2017
---
# <a name="namespaces"></a><span data-ttu-id="1bda5-104">命名空间</span><span class="sxs-lookup"><span data-stu-id="1bda5-104">Namespaces</span></span>

<span data-ttu-id="1bda5-105">命名空间通过使你能够将名称附加一组程序元素，实现将代码整理到相关的功能区域。</span><span class="sxs-lookup"><span data-stu-id="1bda5-105">A namespace lets you organize code into areas of related functionality by enabling you to attach a name to a grouping of program elements.</span></span>


## <a name="syntax"></a><span data-ttu-id="1bda5-106">语法</span><span class="sxs-lookup"><span data-stu-id="1bda5-106">Syntax</span></span>

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a><span data-ttu-id="1bda5-107">备注</span><span class="sxs-lookup"><span data-stu-id="1bda5-107">Remarks</span></span>
<span data-ttu-id="1bda5-108">如果你想要将代码放在一个命名空间，该文件中的第一个声明必须声明命名空间。</span><span class="sxs-lookup"><span data-stu-id="1bda5-108">If you want to put code in a namespace, the first declaration in the file must declare the namespace.</span></span> <span data-ttu-id="1bda5-109">文件的全部内容然后会变得命名空间的一部分。</span><span class="sxs-lookup"><span data-stu-id="1bda5-109">The contents of the entire file then become part of the namespace.</span></span>

<span data-ttu-id="1bda5-110">值和函数，不能直接包含命名空间。</span><span class="sxs-lookup"><span data-stu-id="1bda5-110">Namespaces cannot directly contain values and functions.</span></span> <span data-ttu-id="1bda5-111">相反，必须在模块中，包括值和函数，模块包含在命名空间。</span><span class="sxs-lookup"><span data-stu-id="1bda5-111">Instead, values and functions must be included in modules, and modules are included in namespaces.</span></span> <span data-ttu-id="1bda5-112">命名空间可以包含类型和模块。</span><span class="sxs-lookup"><span data-stu-id="1bda5-112">Namespaces can contain types, modules.</span></span>

<span data-ttu-id="1bda5-113">命名空间可以显式声明命名空间关键字，或隐式声明模块时。</span><span class="sxs-lookup"><span data-stu-id="1bda5-113">Namespaces can be declared explicitly with the namespace keyword, or implicitly when declaring a module.</span></span> <span data-ttu-id="1bda5-114">若要显式声明命名空间，使用命名空间关键字后跟的命名空间名称。</span><span class="sxs-lookup"><span data-stu-id="1bda5-114">To declare a namespace explicitly, use the namespace keyword followed by the namespace name.</span></span> <span data-ttu-id="1bda5-115">下面的示例演示使用类型和模块包含在该命名空间中声明一个命名空间小组件的代码文件。</span><span class="sxs-lookup"><span data-stu-id="1bda5-115">The following example shows a code file that declares a namespace Widgets with a type and a module included in that namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

<span data-ttu-id="1bda5-116">如果该文件的整个内容都位于一个模块，你也可以声明命名空间隐式使用`module`关键字并提供完全限定的模块名称中的新命名空间名称。</span><span class="sxs-lookup"><span data-stu-id="1bda5-116">If the entire contents of the file are in one module, you can also declare namespaces implicitly by using the `module` keyword and providing the new namespace name in the fully qualified module name.</span></span> <span data-ttu-id="1bda5-117">下面的示例演示声明一个命名空间的代码文件`Widgets`和模块`WidgetsModule`，其中包含一个函数。</span><span class="sxs-lookup"><span data-stu-id="1bda5-117">The following example shows a code file that declares a namespace `Widgets` and a module `WidgetsModule`, which contains a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

<span data-ttu-id="1bda5-118">下面的代码是等效于前面的代码，但该模块是一个本地模块声明。</span><span class="sxs-lookup"><span data-stu-id="1bda5-118">The following code is equivalent to the preceding code, but the module is a local module declaration.</span></span> <span data-ttu-id="1bda5-119">在这种情况下，命名空间必须显示在各占一行。</span><span class="sxs-lookup"><span data-stu-id="1bda5-119">In that case, the namespace must appear on its own line.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

<span data-ttu-id="1bda5-120">如果多个模块需要在一个或多个命名空间中的相同文件，则必须使用本地模块声明。</span><span class="sxs-lookup"><span data-stu-id="1bda5-120">If more than one module is required in the same file in one or more namespaces, you must use local module declarations.</span></span> <span data-ttu-id="1bda5-121">当使用本地模块声明时，不能在模块声明中使用限定的命名空间。</span><span class="sxs-lookup"><span data-stu-id="1bda5-121">When you use local module declarations, you cannot use the qualified namespace in the module declarations.</span></span> <span data-ttu-id="1bda5-122">下面的代码演示具有命名空间声明和两个本地模块声明的文件。</span><span class="sxs-lookup"><span data-stu-id="1bda5-122">The following code shows a file that has a namespace declaration and two local module declarations.</span></span> <span data-ttu-id="1bda5-123">在这种情况下，模块会直接包含在该命名空间。没有任何文件具有相同名称的隐式创建的模块。</span><span class="sxs-lookup"><span data-stu-id="1bda5-123">In this case, the modules are contained directly in the namespace; there is no implicitly created module that has the same name as the file.</span></span> <span data-ttu-id="1bda5-124">任何其他代码在文件中，如`do`绑定，属于命名空间中但不是在内部的模块，因此你需要限定模块成员`widgetFunction`通过使用模块名称。</span><span class="sxs-lookup"><span data-stu-id="1bda5-124">Any other code in the file, such as a `do` binding, is in the namespace but not in the inner modules, so you need to qualify the module member `widgetFunction` by using the module name.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

<span data-ttu-id="1bda5-125">此示例的输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="1bda5-125">The output of this example is as follows.</span></span>

```fsharp
Module1 10 20
Module2 5 6
```

<span data-ttu-id="1bda5-126">有关详细信息，请参阅[模块](modules.md)。</span><span class="sxs-lookup"><span data-stu-id="1bda5-126">For more information, see [Modules](modules.md).</span></span>

## <a name="nested-namespaces"></a><span data-ttu-id="1bda5-127">嵌套的命名空间</span><span class="sxs-lookup"><span data-stu-id="1bda5-127">Nested Namespaces</span></span>
<span data-ttu-id="1bda5-128">当你创建一个嵌套命名空间时，则必须完全限定它。</span><span class="sxs-lookup"><span data-stu-id="1bda5-128">When you create a nested namespace, you must fully qualify it.</span></span> <span data-ttu-id="1bda5-129">否则，您创建新的顶级命名空间。</span><span class="sxs-lookup"><span data-stu-id="1bda5-129">Otherwise, you create a new top-level namespace.</span></span> <span data-ttu-id="1bda5-130">在命名空间声明中将忽略缩进。</span><span class="sxs-lookup"><span data-stu-id="1bda5-130">Indentation is ignored in namespace declarations.</span></span>

<span data-ttu-id="1bda5-131">下面的示例演示如何声明嵌套的命名空间。</span><span class="sxs-lookup"><span data-stu-id="1bda5-131">The following example shows how to declare a nested namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a><span data-ttu-id="1bda5-132">在文件和程序集的命名空间</span><span class="sxs-lookup"><span data-stu-id="1bda5-132">Namespaces in Files and Assemblies</span></span>
<span data-ttu-id="1bda5-133">命名空间可以跨多个文件中的单个项目或编译。</span><span class="sxs-lookup"><span data-stu-id="1bda5-133">Namespaces can span multiple files in a single project or compilation.</span></span> <span data-ttu-id="1bda5-134">术语*命名空间片段*描述在一个文件中包含的命名空间的一部分。</span><span class="sxs-lookup"><span data-stu-id="1bda5-134">The term *namespace fragment* describes the part of a namespace that is included in one file.</span></span> <span data-ttu-id="1bda5-135">命名空间还可以跨多个程序集。</span><span class="sxs-lookup"><span data-stu-id="1bda5-135">Namespaces can also span multiple assemblies.</span></span> <span data-ttu-id="1bda5-136">例如，`System`命名空间包括整个.NET Framework 中，也不能跨越多个程序集包含许多嵌套命名空间。</span><span class="sxs-lookup"><span data-stu-id="1bda5-136">For example, the `System` namespace includes the whole .NET Framework, which spans many assemblies and contains many nested namespaces.</span></span>


## <a name="global-namespace"></a><span data-ttu-id="1bda5-137">全局 Namespace</span><span class="sxs-lookup"><span data-stu-id="1bda5-137">Global Namespace</span></span>
<span data-ttu-id="1bda5-138">使用预定义的命名空间`global`放置在.NET 顶级命名空间中的名称。</span><span class="sxs-lookup"><span data-stu-id="1bda5-138">You use the predefined namespace `global` to put names in the .NET top-level namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

<span data-ttu-id="1bda5-139">你还可以使用全局若要引用的顶级的.NET 命名空间，例如，若要解决与其他命名空间的名称冲突。</span><span class="sxs-lookup"><span data-stu-id="1bda5-139">You can also use global to reference the top-level .NET namespace, for example, to resolve name conflicts with other namespaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

##

<span data-ttu-id="1bda5-140">F # 4.1 引入了允许的所有包含的代码要相互递归的命名空间的概念。</span><span class="sxs-lookup"><span data-stu-id="1bda5-140">F# 4.1 introduces the notion of namespaces which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="1bda5-141">这是通过`namespace rec`。</span><span class="sxs-lookup"><span data-stu-id="1bda5-141">This is done via `namespace rec`.</span></span>  <span data-ttu-id="1bda5-142">利用`namespace rec`可以减轻中无法编写类型和模块之间的相互引用代码的一些难题。</span><span class="sxs-lookup"><span data-stu-id="1bda5-142">Use of `namespace rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="1bda5-143">下面是此示例：</span><span class="sxs-lookup"><span data-stu-id="1bda5-143">The following is an example of this:</span></span>

```fsharp
namespace rec MutualReferences

type Orientation = Up | Down
type PeelState = Peeled | Unpeeled

// This exception depends on the type below.
exception DontSqueezeTheBananaException of Banana

type BananaPeel() = class end

type Banana(orientation : Orientation) =
    member val IsPeeled = false with get, set
    member val Orientation = orientation with get, set
    member val Sides: PeelState list = [ Unpeeled; Unpeeled; Unpeeled; Unpeeled] with get, set
    
    member self.Peel() = BananaHelpers.peel self // Note the dependency on the BananaHelpers module.
    member self.SqueezeJuiceOut() = raise (DontSqueezeTheBananaException self) // This member depends on the exception above.

module BananaHelpers =
    let peel (b : Banana) =
        let flip banana =
            match banana.Orientation with
            | Up -> 
                banana.Orientation <- Down
                banana
            | Down -> banana

        let peelSides banana =
            for side in banana.Sides do
                if side = Unpeeled then
                    side <- Peeled

        match b.Orientation with
        | Up ->   b |> flip |> peelSides
        | Down -> b |> peelSides
```

<span data-ttu-id="1bda5-144">请注意，异常`DontSqueezeTheBananaException`和类`Banana`同时相互引用。</span><span class="sxs-lookup"><span data-stu-id="1bda5-144">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="1bda5-145">此外，该模块`BananaHelpers`和类`Banana`也相互引用。</span><span class="sxs-lookup"><span data-stu-id="1bda5-145">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="1bda5-146">这将不可能表示在 F # 中，如果你删除`rec`关键字从`MutualReferences`命名空间。</span><span class="sxs-lookup"><span data-stu-id="1bda5-146">This would not be possible to express in F# if you removed the `rec` keyword from the `MutualReferences` namespace.</span></span>

<span data-ttu-id="1bda5-147">此功能也是可用于顶级[模块](modules.md)在 F # 4.1 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="1bda5-147">This feature is also available for top-level [Modules](modules.md) in F# 4.1 or higher.</span></span>

## <a name="see-also"></a><span data-ttu-id="1bda5-148">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1bda5-148">See Also</span></span>
[<span data-ttu-id="1bda5-149">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="1bda5-149">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="1bda5-150">模块</span><span class="sxs-lookup"><span data-stu-id="1bda5-150">Modules</span></span>](modules.md)

[<span data-ttu-id="1bda5-151">F # RFC FS-1009-允许通过在文件内的较大作用域的互相引用的类型和模块</span><span class="sxs-lookup"><span data-stu-id="1bda5-151">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)