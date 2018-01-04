---
title: "x:Arguments ディレクティブ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
caps.latest.revision: "12"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bb1f5986a0d9f9eb69ade0228925ec06164cee4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="xarguments-directive"></a><span data-ttu-id="ec979-102">x:Arguments ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="ec979-102">x:Arguments Directive</span></span>
<span data-ttu-id="ec979-103">XAML では、既定以外のコンス トラクター オブジェクト要素の宣言またはファクトリ メソッドのオブジェクトの宣言は、パッケージ構築引数。</span><span class="sxs-lookup"><span data-stu-id="ec979-103">Packages construction arguments for a non-default constructor object element declaration in XAML, or for a factory method object declaration.</span></span>  
  
## <a name="xaml-element-usage-nondefault-constructor"></a><span data-ttu-id="ec979-104">XAML 要素の使用 (既定以外のコンス トラクター)</span><span class="sxs-lookup"><span data-stu-id="ec979-104">XAML Element Usage (Nondefault constructor)</span></span>  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a><span data-ttu-id="ec979-105">XAML 要素の使用 (factory method)</span><span class="sxs-lookup"><span data-stu-id="ec979-105">XAML Element Usage (factory method)</span></span>  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="ec979-106">XAML 値</span><span class="sxs-lookup"><span data-stu-id="ec979-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|<span data-ttu-id="ec979-107">既定以外のバッキング コンス トラクターまたはファクトリ メソッドに渡される引数を指定する 1 つまたは複数のオブジェクト要素。</span><span class="sxs-lookup"><span data-stu-id="ec979-107">One or more object elements that specify arguments to be passed to the backing non-default constructor or factory method.</span></span><br /><br /> <span data-ttu-id="ec979-108">一般的な使用では、実際の引数の値を指定するオブジェクトの要素内で初期化のテキストを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec979-108">Typical usage is to use initialization text within the object elements to specify the actual argument values.</span></span> <span data-ttu-id="ec979-109">例のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec979-109">See Examples section.</span></span><br /><br /> <span data-ttu-id="ec979-110">要素の順序は重要です。</span><span class="sxs-lookup"><span data-stu-id="ec979-110">The order of the elements is significant.</span></span> <span data-ttu-id="ec979-111">XAML の型の順序では、型と一致する必要があり、バッキング コンス トラクターまたはファクトリ メソッドのオーバー ロードの順序を入力します。</span><span class="sxs-lookup"><span data-stu-id="ec979-111">The XAML types in order must match the types and type order of the backing constructor or factory method overload.</span></span>|  
|`methodName`|<span data-ttu-id="ec979-112">いずれかを処理するファクトリ メソッドの名前`x:Arguments`引数。</span><span class="sxs-lookup"><span data-stu-id="ec979-112">The name of the factory method that should process any `x:Arguments` arguments.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="ec979-113">依存関係</span><span class="sxs-lookup"><span data-stu-id="ec979-113">Dependencies</span></span>  
 <span data-ttu-id="ec979-114">`x:FactoryMethod`スコープと動作を変更することができます、`x:Arguments`適用されます。</span><span class="sxs-lookup"><span data-stu-id="ec979-114">`x:FactoryMethod` can modify the scope and behavior where `x:Arguments` applies.</span></span>  
  
 <span data-ttu-id="ec979-115">ない場合は`x:FactoryMethod`が指定されている`x:Arguments`バッキング コンス トラクターの代替の (既定値) のシグネチャに適用されます。</span><span class="sxs-lookup"><span data-stu-id="ec979-115">If no `x:FactoryMethod` is specified, `x:Arguments` applies to alternate (non-default) signatures of the backing constructors.</span></span>  
  
 <span data-ttu-id="ec979-116">場合`x:FactoryMethod`が指定されている`x:Arguments`名前のメソッドのオーバー ロードに適用されます。</span><span class="sxs-lookup"><span data-stu-id="ec979-116">If `x:FactoryMethod` is specified, `x:Arguments` applies to an overload of the named method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec979-117">コメント</span><span class="sxs-lookup"><span data-stu-id="ec979-117">Remarks</span></span>  
 <span data-ttu-id="ec979-118">XAML 2006 では、初期化のテキストを既定以外の初期化をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="ec979-118">XAML 2006 can support non-default initialization through initialization text.</span></span> <span data-ttu-id="ec979-119">ただし、初期化のテキストの構築方法の実用的なアプリケーションは制限されます。</span><span class="sxs-lookup"><span data-stu-id="ec979-119">However, the practical application of an initialization text construction technique is limited.</span></span> <span data-ttu-id="ec979-120">初期化のテキストが 1 つのテキスト文字列として扱われますそのため、カスタム情報項目と、文字列からカスタムの区切り記号を解析できる構築動作の型コンバーターが定義されていない場合、1 つのパラメーターの初期化の機能のみ追加します。</span><span class="sxs-lookup"><span data-stu-id="ec979-120">Initialization text is treated as a single text string; therefore, it only adds capability for a single parameter initialization unless a type converter is defined for the construction behavior that can parse custom information items and custom delimiters from the string.</span></span> <span data-ttu-id="ec979-121">また、オブジェクトのロジックをテキスト文字列を場合は true。 文字列以外のプリミティブを処理するための特定の XAML パーサーのネイティブの既定の型コンバーターにすることがあります。</span><span class="sxs-lookup"><span data-stu-id="ec979-121">Also, the text string to object logic is potentially a given XAML parser's native default type converter for handling primitives other than a true string.</span></span>  
  
 <span data-ttu-id="ec979-122">`x:Arguments` XAML の使用法がプロパティ要素の使用、一般的な意味で、ディレクティブのマークアップが含まれるオブジェクト要素の型を参照していないためです。</span><span class="sxs-lookup"><span data-stu-id="ec979-122">The `x:Arguments` XAML usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="ec979-123">では他のディレクティブなど`x:Code`要素に子コンテンツの既定値以外にするマークアップを解釈する範囲境界を定めます場所。</span><span class="sxs-lookup"><span data-stu-id="ec979-123">It is more akin to other directives such as `x:Code` where the element demarks a range in which the markup should be interpreted as other than the default for child contents.</span></span> <span data-ttu-id="ec979-124">オブジェクトの各要素の XAML の型がどの特定のコンス トラクターのファクトリ メソッドのシグネチャを決定する、XAML パーサーで使用される引数の型に関する情報がどのように通信するこの例では、`x:Arguments`参照しようとして使用します。</span><span class="sxs-lookup"><span data-stu-id="ec979-124">In this case, the XAML type of each object element communicates information about the argument types, which is used by XAML parsers to determine which specific constructor factory method signature an `x:Arguments` usage is attempting to reference.</span></span>  
  
 <span data-ttu-id="ec979-125">`x:Arguments`オブジェクト要素の構築される必要がありますの前に、他のプロパティ要素、コンテンツ、内部のテキスト、またはオブジェクト要素の初期化の文字列。</span><span class="sxs-lookup"><span data-stu-id="ec979-125">`x:Arguments` for an object element being constructed must precede any other property elements, content, inner text, or initialization strings of the object element.</span></span> <span data-ttu-id="ec979-126">内のオブジェクト要素`x:Arguments`その XAML の型とそのバッキング コンス トラクターまたはファクトリ メソッドによって許可されている属性および初期化文字列を含むことができます。</span><span class="sxs-lookup"><span data-stu-id="ec979-126">The object elements within `x:Arguments` can include attributes and initialization strings, as permitted by that XAML type and its backing constructor or factory method.</span></span> <span data-ttu-id="ec979-127">オブジェクトまたは引数のいずれかのカスタム XAML の型または外側にあるそれ以外の場合、既定の XAML 名前空間によって確立されたプレフィックスのマッピングを参照する XAML の型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ec979-127">For either the object or the arguments, you can specify custom XAML types or XAML types that are otherwise outside the default XAML namespace by referencing established prefix mappings.</span></span>  
  
 <span data-ttu-id="ec979-128">XAML プロセッサに引数を指定する方法を決定する、次のガイドラインを使用して`x:Arguments`オブジェクトを構築するために使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec979-128">XAML processors use the following guidelines to determine how the arguments specified in `x:Arguments` should be used to construct an object.</span></span> <span data-ttu-id="ec979-129">場合`x:FactoryMethod`が指定されている情報と比較を指定した`x:FactoryMethod`(なおの値`x:FactoryMethod`メソッド名であり、名前付きメソッドはオーバー ロードを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="ec979-129">If `x:FactoryMethod` is specified, information is compared to the specified `x:FactoryMethod` (note that the value of `x:FactoryMethod` is the method name, and the named method can have overloads.</span></span> <span data-ttu-id="ec979-130">場合`x:FactoryMethod`が指定されていない、一連のオブジェクトのすべてのパブリック コンス トラクター オーバー ロードに情報を比較します。</span><span class="sxs-lookup"><span data-stu-id="ec979-130">If `x:FactoryMethod` is not specified, information is compared to the set of all public constructor overloads of the object.</span></span> <span data-ttu-id="ec979-131">XAML の処理ロジックは、パラメーターの数を比較し、アリティが一致するオーバー ロードを選択します。</span><span class="sxs-lookup"><span data-stu-id="ec979-131">XAML processing logic then compares the number of parameters and selects the overload with matching arity.</span></span> <span data-ttu-id="ec979-132">複数の一致がある場合、XAML プロセッサは必要があります指定されたオブジェクトの要素の XAML の型に基づくパラメーターの型を比較します。</span><span class="sxs-lookup"><span data-stu-id="ec979-132">If there is more than one match, the XAML processor should compare the types of the parameters based on the XAML types of the provided object elements.</span></span> <span data-ttu-id="ec979-133">複数のまま 1 つの一致がある場合は、XAML プロセッサの動作は定義されません。</span><span class="sxs-lookup"><span data-stu-id="ec979-133">If there is still more than one match, the XAML processor behavior is undefined.</span></span> <span data-ttu-id="ec979-134">場合、`x:FactoryMethod`が指定されているメソッドを解決することはできませんが、XAML プロセッサは、例外をスローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec979-134">If a `x:FactoryMethod` is specified but the method cannot be resolved, a XAML processor should throw an exception.</span></span>  
  
 <span data-ttu-id="ec979-135">XAML 属性の使用方法`<x:Arguments>string</x:Arguments>`は技術的に可能です。</span><span class="sxs-lookup"><span data-stu-id="ec979-135">A XAML attribute usage `<x:Arguments>string</x:Arguments>` is technically possible.</span></span> <span data-ttu-id="ec979-136">ただし、これにより、ありませんでした何それ以外の場合の初期化のテキストと型コンバーターを使ってれない機能と、この構文を使用して XAML 2009 のファクトリ メソッドの機能の目的で設計ではありません。</span><span class="sxs-lookup"><span data-stu-id="ec979-136">However, this provides no capabilities beyond what could be done otherwise through initialization text and type converters, and using this syntax is not the design intention of the XAML 2009 factory method features.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ec979-137">使用例</span><span class="sxs-lookup"><span data-stu-id="ec979-137">Examples</span></span>  
 <span data-ttu-id="ec979-138">次の例は、署名、次の XAML の使用方法に既定以外のコンス トラクターを示します`x:Arguments`そのシグネチャにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="ec979-138">The following example shows a non-default constructor signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
```csharp  
public class Food {  
    private string _name;  
    private Int32 _calories;  
    public Food(string name, Int32 calories) {  
        _name=name;  
        _calories=calories;  
    }  
}  
```  
  
```xaml  
<my:Food>  
    <x:Arguments>  
        <x:String>Apple</x:String>  
        <x:Int32>150</x:Int32>  
    </x:Arguments>  
</my:Food>  
```  
  
 <span data-ttu-id="ec979-139">次の例では、ターゲット工場出荷時のメソッド シグネチャでは、次の XAML の使用方法を示しています。`x:Arguments`そのシグネチャにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="ec979-139">The following example shows a target factory method signature, then the XAML usage of `x:Arguments` that accesses that signature.</span></span>  
  
```csharp  
public Food TryLookupFood(string name)  
{  
  switch (name) {  
    case "Apple": return new Food("Apple",150);  
    case "Chocolate": return new Food("Chocolate",200);  
    case "Cheese": return new Food("Cheese", 450);  
    default: {return new Food(name,0);  
  }  
}  
```  
  
```xaml  
<my:Food x:FactoryMethod="TryLookupFood">  
    <x:Arguments>  
        <x:String>Apple</x:String>  
    </x:Arguments>  
</my:Food>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec979-140">参照</span><span class="sxs-lookup"><span data-stu-id="ec979-140">See Also</span></span>  
 [<span data-ttu-id="ec979-141">.NET Framework XAML サービスで使用するためのカスタム型の定義</span><span class="sxs-lookup"><span data-stu-id="ec979-141">Defining Custom Types for Use with .NET Framework XAML Services</span></span>](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)  
 [<span data-ttu-id="ec979-142">XAML の概要 (WPF)</span><span class="sxs-lookup"><span data-stu-id="ec979-142">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
