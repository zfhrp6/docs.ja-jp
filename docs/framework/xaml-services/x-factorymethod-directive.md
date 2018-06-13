---
title: x:FactoryMethod ディレクティブ
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 75225e624abdd3dc0862a04fae409da48b3f0d1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563416"
---
# <a name="xfactorymethod-directive"></a><span data-ttu-id="adc10-102">x:FactoryMethod ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="adc10-102">x:FactoryMethod Directive</span></span>
<span data-ttu-id="adc10-103">XAML プロセッサが、バッキング型の解決後、オブジェクトを初期化するために使用するコンス トラクター以外の方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="adc10-103">Specifies a method other than a constructor that a XAML processor should use to initialize an object after resolving its backing type.</span></span>  
  
## <a name="xaml-attribute-usage-no-xarguments"></a><span data-ttu-id="adc10-104">XAML 属性の使用方法、x: 引数なし</span><span class="sxs-lookup"><span data-stu-id="adc10-104">XAML Attribute Usage, no x:Arguments</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a><span data-ttu-id="adc10-105">XAML 属性の使用方法、要素として X:arguments</span><span class="sxs-lookup"><span data-stu-id="adc10-105">XAML Attribute Usage, x:Arguments as Element(s)</span></span>  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="adc10-106">XAML 値</span><span class="sxs-lookup"><span data-stu-id="adc10-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`methodname`|<span data-ttu-id="adc10-107">XAML プロセッサは、として指定されたインスタンスを初期化するために呼び出すメソッドの文字列のメソッド名`object`です。</span><span class="sxs-lookup"><span data-stu-id="adc10-107">The string method name of a method that XAML processors call to initialize the instance specified as `object`.</span></span> <span data-ttu-id="adc10-108">「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="adc10-108">See Remarks.</span></span>|  
|`oneOrMoreObjectElements`|<span data-ttu-id="adc10-109">ファクトリ メソッドのパラメーターを指定するオブジェクトのオブジェクトの要素の 1 つ以上</span><span class="sxs-lookup"><span data-stu-id="adc10-109">One or more object elements for objects that specify factory method parameters.</span></span> <span data-ttu-id="adc10-110">順序は重要です。ファクトリ メソッドに引数を渡す必要があります、順序を示します。</span><span class="sxs-lookup"><span data-stu-id="adc10-110">Order is significant; it signifies the order in which arguments should be passed to the factory method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adc10-111">コメント</span><span class="sxs-lookup"><span data-stu-id="adc10-111">Remarks</span></span>  
 <span data-ttu-id="adc10-112">場合`methodname`インスタンス メソッドでは、修飾することはできません。</span><span class="sxs-lookup"><span data-stu-id="adc10-112">If `methodname` is an instance method, it cannot be qualified.</span></span>  
  
 <span data-ttu-id="adc10-113">ファクトリ メソッドと静的メソッドがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="adc10-113">Static methods as factory methods are supported.</span></span> <span data-ttu-id="adc10-114">場合`methodname`静的メソッドでは、`methodname`として提供される、 *typeName*.*methodName*の組み合わせを*typeName*静的ファクトリ メソッドを定義するクラスの名前します。</span><span class="sxs-lookup"><span data-stu-id="adc10-114">If `methodname` is a static method, `methodname` is provided as a *typeName*.*methodName* combination, where *typeName* names the class that defines the static factory method.</span></span> <span data-ttu-id="adc10-115">*typeName*マップされた xmlns で型を参照している場合のプレフィックスで修飾することができます。</span><span class="sxs-lookup"><span data-stu-id="adc10-115">*typeName* can be prefix-qualified if referring to a type in a mapped xmlns.</span></span> <span data-ttu-id="adc10-116">*typeName*とは異なる型を指定できます`typeof(``object``)`です。</span><span class="sxs-lookup"><span data-stu-id="adc10-116">*typeName* can be a different type than `typeof(``object``)`.</span></span>  
  
 <span data-ttu-id="adc10-117">工場出荷時のメソッドは、関連するオブジェクトの要素をサポートする型の宣言されたパブリック メソッドである必要があります。</span><span class="sxs-lookup"><span data-stu-id="adc10-117">The factory method must be a declared public method of the type that backs the relevant object element.</span></span>  
  
 <span data-ttu-id="adc10-118">工場出荷時のメソッドは、関連するオブジェクトに割り当てることができるインスタンスを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="adc10-118">The factory method must return an instance that is assignable to the relevant object.</span></span> <span data-ttu-id="adc10-119">ファクトリ メソッドにする必要があります null を返すことはありません。</span><span class="sxs-lookup"><span data-stu-id="adc10-119">Factory methods should never return null.</span></span>  
  
 <span data-ttu-id="adc10-120">`x:Arguments` ファクトリ メソッドのシグネチャに最も適しているの原則で動作します。</span><span class="sxs-lookup"><span data-stu-id="adc10-120">`x:Arguments` operates on a principle of best match for signatures of factory methods.</span></span> <span data-ttu-id="adc10-121">パラメーターの数を最初に評価に一致します。</span><span class="sxs-lookup"><span data-stu-id="adc10-121">Matching evaluates the parameter count first.</span></span> <span data-ttu-id="adc10-122">パラメーターの数に一致する 1 つ以上の場合は、パラメーターの型がで評価されると最適な組み合わせが決定されます。</span><span class="sxs-lookup"><span data-stu-id="adc10-122">If there is more than one possible match for a parameter count, parameter type is then evaluated and best match is determined.</span></span> <span data-ttu-id="adc10-123">評価のこのフェーズの後にあいまいさが残る、XAML プロセッサの動作は未定義です。</span><span class="sxs-lookup"><span data-stu-id="adc10-123">If there is still ambiguity after this phase of evaluation, XAML processor behavior is undefined.</span></span>  
  
 <span data-ttu-id="adc10-124">`x:FactoryMethod`要素の使用法がプロパティ要素の使用、一般的な意味で、ディレクティブのマークアップが含まれるオブジェクト要素の型を参照していないためです。</span><span class="sxs-lookup"><span data-stu-id="adc10-124">The `x:FactoryMethod` element usage is not property element usage in the typical sense, because the directive markup does not reference the containing object element's type.</span></span> <span data-ttu-id="adc10-125">推測要素の使用方法は、属性の使用方法ほど一般的です。</span><span class="sxs-lookup"><span data-stu-id="adc10-125">It is expected that element usage is less common than attribute usage.</span></span> <span data-ttu-id="adc10-126">`x:Arguments` と共に使用できます (属性または要素のいずれかの利用率)`x:FactoryMethod`要素の使用方法が、これは具体的には表示されません使用状況のセクションでします。</span><span class="sxs-lookup"><span data-stu-id="adc10-126">`x:Arguments` (either attribute or element usage) can be used along with `x:FactoryMethod` element usage, but this is not specifically shown in the Usage sections.</span></span>  
  
 <span data-ttu-id="adc10-127">`x:FactoryMethod` 要素には、その他のすべてのプロパティ要素が前に指定する必要があります、としてはいずれかで始まる必要があります`x:Arguments`も、要素として提供されており、コンテンツ/内部のテキスト/初期化のテキストの前にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="adc10-127">`x:FactoryMethod` as an element must precede any other property elements, must precede any `x:Arguments` also provided as elements, and must precede any content/inner text/initialization text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adc10-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="adc10-128">See Also</span></span>  
 [<span data-ttu-id="adc10-129">x:Arguments ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="adc10-129">x:Arguments Directive</span></span>](../../../docs/framework/xaml-services/x-arguments-directive.md)
