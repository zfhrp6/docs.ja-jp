---
title: "x:Reference のマークアップ拡張機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 06e59e7686004f8fd44473bd9572ed07a0118d1f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="xreference-markup-extension"></a><span data-ttu-id="78a87-102">x:Reference のマークアップ拡張機能</span><span class="sxs-lookup"><span data-stu-id="78a87-102">x:Reference Markup Extension</span></span>
<span data-ttu-id="78a87-103">XAML マークアップの他の場所で宣言されているインスタンスを参照します。</span><span class="sxs-lookup"><span data-stu-id="78a87-103">References an instance that is declared elsewhere in XAML markup.</span></span> <span data-ttu-id="78a87-104">要素の参照を参照`x:Name`です。</span><span class="sxs-lookup"><span data-stu-id="78a87-104">The reference refers to an element's `x:Name`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="78a87-105">XAML 属性の使用方法</span><span class="sxs-lookup"><span data-stu-id="78a87-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Reference instancexName}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="78a87-106">XAML オブジェクト要素の使用方法</span><span class="sxs-lookup"><span data-stu-id="78a87-106">XAML Object Element Usage</span></span>  
  
```xaml  
<object>  
  <object.property>  
    <x:Reference Name="instancexName"/>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="78a87-107">XAML 値</span><span class="sxs-lookup"><span data-stu-id="78a87-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`instancexName`|<span data-ttu-id="78a87-108">`x:Name`値 (またはの値、 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-プロパティを識別) の参照先のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="78a87-108">The `x:Name` value (or value of the <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>-identified property) of the referenced instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78a87-109">コメント</span><span class="sxs-lookup"><span data-stu-id="78a87-109">Remarks</span></span>  
 <span data-ttu-id="78a87-110">`x:Reference`WPF などの特定のフレームワークで実装された場合は要素の参照の概念の XAML 言語レベルのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="78a87-110">`x:Reference` provides XAML language-level support for an element reference concept that was otherwise implemented in specific frameworks such as WPF.</span></span>  
  
## <a name="xreference-and-wpf"></a><span data-ttu-id="78a87-111">X:reference と WPF</span><span class="sxs-lookup"><span data-stu-id="78a87-111">x:Reference and WPF</span></span>  
 <span data-ttu-id="78a87-112">WPF XAML 2006 では、要素の参照は、フレームワーク レベルの機能のによってアドレス指定<xref:System.Windows.Data.Binding.ElementName%2A>バインドします。</span><span class="sxs-lookup"><span data-stu-id="78a87-112">In WPF and XAML 2006, element references are addressed by the framework-level feature of <xref:System.Windows.Data.Binding.ElementName%2A> binding.</span></span> <span data-ttu-id="78a87-113">ほとんどの WPF アプリケーションおよびシナリオ、<xref:System.Windows.Data.Binding.ElementName%2A>バインディングを引き続き使用します。</span><span class="sxs-lookup"><span data-stu-id="78a87-113">For most WPF applications and scenarios, <xref:System.Windows.Data.Binding.ElementName%2A> binding should still be used.</span></span> <span data-ttu-id="78a87-114">この一般的なガイダンスの例外は、データ コンテキストまたは不可能な場合のデータ バインディングを構成するスコープの他の考慮事項があるおよびマークアップのコンパイルが関係していない、ケースにすることがあります。</span><span class="sxs-lookup"><span data-stu-id="78a87-114">Exceptions to this general guidance might include cases where there are data context or other scoping considerations that make data binding impractical and where markup compilation is not involved.</span></span>  
  
 <span data-ttu-id="78a87-115">`x:Reference`XAML 2009 では、コンス トラクターが定義されます。</span><span class="sxs-lookup"><span data-stu-id="78a87-115">`x:Reference` is a construct defined in XAML 2009.</span></span> <span data-ttu-id="78a87-116">WPF では XAML 2009 の機能を使用できますが、WPF マークアップ コンパイルされていない XAML に限定されます。</span><span class="sxs-lookup"><span data-stu-id="78a87-116">In WPF, you can use XAML 2009 features, but only for XAML that is not WPF markup-compiled.</span></span> <span data-ttu-id="78a87-117">マークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 言語のキーワードと機能をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="78a87-117">Markup-compiled XAML and the BAML form of XAML do not currently support the XAML 2009 language keywords and features.</span></span>
