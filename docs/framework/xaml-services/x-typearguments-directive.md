---
title: "x:TypeArguments ディレクティブ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
caps.latest.revision: "18"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: a63a8080c71ad026664e2e14fc1762fcdd4bdb36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xtypearguments-directive"></a><span data-ttu-id="0cf98-102">x:TypeArguments ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="0cf98-102">x:TypeArguments Directive</span></span>
<span data-ttu-id="0cf98-103">パスの制約は、ジェネリック型のコンス トラクターにジェネリック型の引数を入力します。</span><span class="sxs-lookup"><span data-stu-id="0cf98-103">Passes constraining type arguments of a generic to the constructor of the generic type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="0cf98-104">XAML 属性の使用方法</span><span class="sxs-lookup"><span data-stu-id="0cf98-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="0cf98-105">XAML 値</span><span class="sxs-lookup"><span data-stu-id="0cf98-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`object`|<span data-ttu-id="0cf98-106">CLR のジェネリック型によってサポートされる XAML 型のオブジェクト要素の宣言。</span><span class="sxs-lookup"><span data-stu-id="0cf98-106">An object element declaration of a XAML type, which is backed by a CLR generic type.</span></span> <span data-ttu-id="0cf98-107">場合`object`は既定の XAML 名前空間ではない XAML 型を参照`object`XAML 名前空間を示すためにプレフィックスが必要です、`object`が存在します。</span><span class="sxs-lookup"><span data-stu-id="0cf98-107">If `object` refers to a XAML type that is not from the default XAML namespace, `object` requires a prefix to indicate the XAML namespace where `object` exists.</span></span>|  
|`typeString`|<span data-ttu-id="0cf98-108">1 つまたは複数の XAML を宣言する文字列は、CLR のジェネリック型の型引数を指定する文字列で名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="0cf98-108">A string that declares one or more XAML type names as strings, which supplies the type arguments for the CLR generic type.</span></span> <span data-ttu-id="0cf98-109">追加の構文のノートの「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0cf98-109">See Remarks for additional syntax notes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cf98-110">コメント</span><span class="sxs-lookup"><span data-stu-id="0cf98-110">Remarks</span></span>  
 <span data-ttu-id="0cf98-111">ほとんどの場合、XAML の型情報の項目として使用される、`typeString`文字列の先頭には、します。</span><span class="sxs-lookup"><span data-stu-id="0cf98-111">In most cases, the XAML types that are used as an information item in a `typeString` string are prefixed.</span></span> <span data-ttu-id="0cf98-112">一般的な種類の CLR ジェネリック制約 (たとえば、<xref:System.Int32>と<xref:System.String>) CLR 基底クラス ライブラリから取得します。</span><span class="sxs-lookup"><span data-stu-id="0cf98-112">Typical types of CLR generic constraints (for example, <xref:System.Int32> and <xref:System.String>) come from CLR base class libraries.</span></span> <span data-ttu-id="0cf98-113">これらのライブラリを使用して、フレームワーク固有の標準的なマップの既定の XAML 名前空間ではありません、したがって、XAML の使用方法のプレフィックスのマッピングが必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cf98-113">Those libraries are not mapped to typical framework-specific default XAML namespaces, and therefore, require a prefix mapping for XAML usage.</span></span>  
  
 <span data-ttu-id="0cf98-114">コンマ区切り記号を使用して、1 つ以上の XAML 型名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0cf98-114">You can specify more than one XAML type name by using a comma delimiter.</span></span>  
  
 <span data-ttu-id="0cf98-115">ジェネリック制約自体がジェネリック型を使用する場合、入れ子になった制約の型引数はかっこ () で含まれていることができます。</span><span class="sxs-lookup"><span data-stu-id="0cf98-115">If the generic constraints themselves use generic types, the nested constraint type arguments can be contained by parentheses ().</span></span>  
  
 <span data-ttu-id="0cf98-116">なおのこの定義`x:TypeArguments`が .NET Framework XAML サービスに固有で CLR バッキングを使用しています。</span><span class="sxs-lookup"><span data-stu-id="0cf98-116">Note that this definition of `x:TypeArguments` is specific to .NET Framework XAML Services and using CLR backing.</span></span> <span data-ttu-id="0cf98-117">言語レベルの定義は含まれて[ \[MS-XAML\]セクション 5.3.11](http://go.microsoft.com/fwlink/?LinkId=114525)です。</span><span class="sxs-lookup"><span data-stu-id="0cf98-117">A language-level definition can be found in [\[MS-XAML\] Section 5.3.11](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="usage-examples"></a><span data-ttu-id="0cf98-118">使用例</span><span class="sxs-lookup"><span data-stu-id="0cf98-118">Usage Examples</span></span>  
 <span data-ttu-id="0cf98-119">これらの例については、次の XAML 名前空間の定義が宣言されていることを想定します。</span><span class="sxs-lookup"><span data-stu-id="0cf98-119">For these examples, assume that the following XAML namespace definitions are declared:</span></span>  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a><span data-ttu-id="0cf98-120">リスト\<文字列 ></span><span class="sxs-lookup"><span data-stu-id="0cf98-120">List\<String></span></span>  
 <span data-ttu-id="0cf98-121">`<scg:List x:TypeArguments="sys:String" ...>`新しいインスタンスを作成<xref:System.Collections.Generic.List%601>で、<xref:System.String>引数を入力します。</span><span class="sxs-lookup"><span data-stu-id="0cf98-121">`<scg:List x:TypeArguments="sys:String" ...>` instantiates a new <xref:System.Collections.Generic.List%601> with a <xref:System.String> type argument.</span></span>  
  
### <a name="dictionarystringstring"></a><span data-ttu-id="0cf98-122">ディクショナリ\<String, String ></span><span class="sxs-lookup"><span data-stu-id="0cf98-122">Dictionary\<String,String></span></span>  
 <span data-ttu-id="0cf98-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`新しいインスタンスを作成<xref:System.Collections.Generic.Dictionary%602>、2 つ<xref:System.String>引数を入力します。</span><span class="sxs-lookup"><span data-stu-id="0cf98-123">`<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` instantiates a new <xref:System.Collections.Generic.Dictionary%602> with two <xref:System.String> type arguments.</span></span>  
  
### <a name="queuekeyvaluepairstringstring"></a><span data-ttu-id="0cf98-124">キュー < KeyValuePair\<String, String >></span><span class="sxs-lookup"><span data-stu-id="0cf98-124">Queue<KeyValuePair\<String,String>></span></span>  
 <span data-ttu-id="0cf98-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`新しいインスタンスを作成<xref:System.Collections.Generic.Queue%601>の制約を持つ<xref:System.Collections.Generic.KeyValuePair%602>内部制約の型引数を持つ<xref:System.String>と<xref:System.String>です。</span><span class="sxs-lookup"><span data-stu-id="0cf98-125">`<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` instantiates a new <xref:System.Collections.Generic.Queue%601> that has a constraint of <xref:System.Collections.Generic.KeyValuePair%602> with the inner constraint type arguments <xref:System.String> and <xref:System.String>.</span></span>  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a><span data-ttu-id="0cf98-126">XAML 2006 および WPF の汎用的な XAML の使用</span><span class="sxs-lookup"><span data-stu-id="0cf98-126">XAML 2006 and WPF Generic XAML Usages</span></span>  
 <span data-ttu-id="0cf98-127">XAML 2006 の使用状況、および WPF アプリケーションに使用される XAML では、次の制限が存在して`x:TypeArguments`と一般的な XAML からジェネリック型の使用法。</span><span class="sxs-lookup"><span data-stu-id="0cf98-127">For XAML 2006 usage, and XAML that is used for WPF applications, the following restrictions exist for `x:TypeArguments` and generic type usages from XAML in general:</span></span>  
  
-   <span data-ttu-id="0cf98-128">XAML ファイルのルート要素だけでは、ジェネリック型を参照する汎用的な XAML の使用方法をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="0cf98-128">Only the root element of a XAML file can support a generic XAML usage that references a generic type.</span></span>  
  
-   <span data-ttu-id="0cf98-129">ルート要素は、少なくとも 1 つの型引数を持つジェネリック型にマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cf98-129">The root element must map to a generic type with at least one type argument.</span></span> <span data-ttu-id="0cf98-130">例としては<xref:System.Windows.Navigation.PageFunction%601>します。</span><span class="sxs-lookup"><span data-stu-id="0cf98-130">An example is <xref:System.Windows.Navigation.PageFunction%601>.</span></span> <span data-ttu-id="0cf98-131">ページ関数は、wpf XAML ジェネリックの使用状況のサポートの主なシナリオです。</span><span class="sxs-lookup"><span data-stu-id="0cf98-131">The page functions are the primary scenario for XAML generic usage support in WPF.</span></span>  
  
-   <span data-ttu-id="0cf98-132">ジェネリックのルート要素の XAML オブジェクト要素は、部分クラスを使用しても宣言しなければなりません`x:Class`です。</span><span class="sxs-lookup"><span data-stu-id="0cf98-132">The root element XAML object element for the generic must also declare a partial class using `x:Class`.</span></span> <span data-ttu-id="0cf98-133">これは、ビルド アクションを WPF を定義する場合でも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="0cf98-133">This is true even if defining a WPF build action.</span></span>  
  
-   <span data-ttu-id="0cf98-134">`x:TypeArguments`入れ子になったジェネリック制約は参照できません。</span><span class="sxs-lookup"><span data-stu-id="0cf98-134">`x:TypeArguments` cannot reference nested generic constraints.</span></span>  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a><span data-ttu-id="0cf98-135">XAML 2009 またはなし、WPF 3.0 または 3.5 を WPF XAML 2006 の依存関係</span><span class="sxs-lookup"><span data-stu-id="0cf98-135">XAML 2009 or XAML 2006 with No WPF 3.0 or WPF 3.5 Dependency</span></span>  
 <span data-ttu-id="0cf98-136">XAML 2006 または XAML 2009 のいずれかの .NET Framework XAML サービスでは、WPF に関連する汎用の XAML 使用量に制限が緩和されています。</span><span class="sxs-lookup"><span data-stu-id="0cf98-136">In .NET Framework XAML Services for either XAML 2006 or XAML 2009, the WPF-related restrictions on generic XAML usage are relaxed.</span></span> <span data-ttu-id="0cf98-137">XAML マークアップ、バッキング型システムとオブジェクト モデルをサポートする任意の位置に汎用オブジェクトの要素をインスタンス化することができます。</span><span class="sxs-lookup"><span data-stu-id="0cf98-137">You can instantiate a generic object element at any position in XAML markup that the backing type system and object model can support.</span></span>  
  
 <span data-ttu-id="0cf98-138">XAML 2009 を使用する場合は、CLR のマッピングではなく基本データ型を共通言語プリミティブの XAML 型を取得する、使用することができます[共通の XAML 言語プリミティブの組み込み型](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)内の情報項目として、`typeString`です。</span><span class="sxs-lookup"><span data-stu-id="0cf98-138">If you use XAML 2009 instead of mapping the CLR base types to obtain XAML types for common language primitives, you can use [Built-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) as information items in a `typeString`.</span></span> <span data-ttu-id="0cf98-139">たとえば、次を宣言する可能性があります (表示されませんが、プレフィックスのマッピングが x は XAML 2009 の XAML 言語の XAML 名前空間)。</span><span class="sxs-lookup"><span data-stu-id="0cf98-139">For example, you could declare the following (prefix mappings not shown, but x is the XAML language XAML namespace for XAML 2009):</span></span>  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 <span data-ttu-id="0cf98-140">WPF では、対象とするときに[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]、と共に XAML 2009 の機能を使用する`x:TypeArguments`loose XAML (XAML をマークアップ コンパイルされていない) に対してのみです。</span><span class="sxs-lookup"><span data-stu-id="0cf98-140">In WPF and when targeting [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use XAML 2009 features together with `x:TypeArguments` but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="0cf98-141">WPF 向けにマークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 のキーワードと機能をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="0cf98-141">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span> <span data-ttu-id="0cf98-142">必要なマークアップをコンパイルした場合、XAML は、「XAML 2006 および WPF 汎用 XAML の使用」セクションで説明した制限で動作する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cf98-142">If you need to markup compile the XAML, you must operate under the restrictions noted in the "XAML 2006 and WPF Generic XAML Usages" section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cf98-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="0cf98-143">See Also</span></span>  
 [<span data-ttu-id="0cf98-144">x:Class ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="0cf98-144">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="0cf98-145">x:Type マークアップ拡張機能</span><span class="sxs-lookup"><span data-stu-id="0cf98-145">x:Type Markup Extension</span></span>](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [<span data-ttu-id="0cf98-146">共通の XAML 言語プリミティブの組み込み型</span><span class="sxs-lookup"><span data-stu-id="0cf98-146">Built-in Types for Common XAML Language Primitives</span></span>](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)  
 [<span data-ttu-id="0cf98-147">XAML のジェネリック</span><span class="sxs-lookup"><span data-stu-id="0cf98-147">Generics in XAML</span></span>](../../../docs/framework/xaml-services/generics-in-xaml.md)
