---
title: '方法 : 依存関係プロパティを実装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: b0c5b33d841f43249f9559bd31f1ef8fe66ff05e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544649"
---
# <a name="how-to-implement-a-dependency-property"></a><span data-ttu-id="c4f06-102">方法 : 依存関係プロパティを実装する</span><span class="sxs-lookup"><span data-stu-id="c4f06-102">How to: Implement a Dependency Property</span></span>
<span data-ttu-id="c4f06-103">この例は、バックアップする方法を示しています、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]を持つプロパティ、<xref:System.Windows.DependencyProperty>フィールド、ため、依存関係プロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="c4f06-103">This example shows how to back a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] property with a <xref:System.Windows.DependencyProperty> field, thus defining a dependency property.</span></span> <span data-ttu-id="c4f06-104">独自に定義したプロパティが [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のさまざまな機能、たとえばスタイル、データ バインディング、継承、アニメーション、既定値をサポートできるようにするには、そのプロパティを依存関係プロパティとして実装します。</span><span class="sxs-lookup"><span data-stu-id="c4f06-104">When you define your own properties and want them to support many aspects of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] functionality, including styles, data binding, inheritance, animation, and default values, you should implement them as a dependency property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4f06-105">例</span><span class="sxs-lookup"><span data-stu-id="c4f06-105">Example</span></span>  
 <span data-ttu-id="c4f06-106">次の例は最初に呼び出すことによって、依存関係プロパティを登録、<xref:System.Windows.DependencyProperty.Register%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="c4f06-106">The following example first registers a dependency property by calling the <xref:System.Windows.DependencyProperty.Register%2A> method.</span></span> <span data-ttu-id="c4f06-107">名前の格納に使用して、依存関係プロパティの特性がある必要がある識別子のフィールドの名前、<xref:System.Windows.DependencyProperty.Name%2A>の依存関係プロパティの一部として選択した、<xref:System.Windows.DependencyProperty.Register%2A>呼び出し、リテラル文字列により追加された`Property`です。</span><span class="sxs-lookup"><span data-stu-id="c4f06-107">The name of the identifier field that you use to store the name and characteristics of the dependency property must be the <xref:System.Windows.DependencyProperty.Name%2A> you chose for the dependency property as part of the <xref:System.Windows.DependencyProperty.Register%2A> call, appended by the literal string `Property`.</span></span> <span data-ttu-id="c4f06-108">インスタンスとの依存関係プロパティを登録する場合、<xref:System.Windows.DependencyProperty.Name%2A>の`Location`、依存関係プロパティを定義する識別子のフィールドにという名前を付ける`LocationProperty`です。</span><span class="sxs-lookup"><span data-stu-id="c4f06-108">For instance, if you register a dependency property with a <xref:System.Windows.DependencyProperty.Name%2A> of `Location`, then the identifier field that you define for the dependency property must be named `LocationProperty`.</span></span>  
  
 <span data-ttu-id="c4f06-109">この例では、依存関係プロパティの名前とその[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]アクセサーが`State`; 識別子フィールドは`StateProperty`; プロパティの型は<xref:System.Boolean>; 依存関係プロパティを登録する型、および`MyStateControl`です。</span><span class="sxs-lookup"><span data-stu-id="c4f06-109">In this example, the name of the dependency property and its [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] accessor is `State`; the identifier field is `StateProperty`; the type of the property is <xref:System.Boolean>; and the type that registers the dependency property is `MyStateControl`.</span></span>  
  
 <span data-ttu-id="c4f06-110">このパターンに従って名前が付けられていない場合は、定義したプロパティがデザイナーから正しく報告されず、プロパティ システムのスタイル適用の一部が予期したとおりに動作しなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c4f06-110">If you fail to follow this naming pattern, designers might not report your property correctly, and certain aspects of property system style application might not behave as expected.</span></span>  
  
 <span data-ttu-id="c4f06-111">依存関係プロパティの既定のメタデータを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="c4f06-111">You can also specify default metadata for a dependency property.</span></span> <span data-ttu-id="c4f06-112">`State` 依存関係プロパティの既定値を `false` として登録する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c4f06-112">This example registers the default value of the `State` dependency property to be `false`.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 <span data-ttu-id="c4f06-113">単にプライベート フィールドを使用して [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] プロパティを補足するのではなく依存関係プロパティを実装する理由とその方法の詳細については、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c4f06-113">For more information about how and why to implement a dependency property, as opposed to just backing a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property with a private field, see [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4f06-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4f06-114">See Also</span></span>  
 [<span data-ttu-id="c4f06-115">依存関係プロパティの概要</span><span class="sxs-lookup"><span data-stu-id="c4f06-115">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="c4f06-116">方法トピック</span><span class="sxs-lookup"><span data-stu-id="c4f06-116">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
