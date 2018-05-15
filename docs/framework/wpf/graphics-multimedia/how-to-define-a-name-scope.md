---
title: '方法 : 名前のスコープを定義する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- name scope [WPF], defining
- Storyboards [WPF], animating in procedural code
- animation [WPF], Storyboards [WPF], in procedural code
ms.assetid: 4f361925-6a08-40dc-8231-a61111c6b28b
ms.openlocfilehash: 689c8187fcf17ef48a73bc5a6fc4928f3be1a078
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-a-name-scope"></a><span data-ttu-id="95e34-102">方法 : 名前のスコープを定義する</span><span class="sxs-lookup"><span data-stu-id="95e34-102">How to: Define a Name Scope</span></span>
<span data-ttu-id="95e34-103">使用してアニメーション化<xref:System.Windows.Media.Animation.Storyboard>コードでは、作成する必要があります、<xref:System.Windows.NameScope>し、その名前のスコープを所有する要素を持つターゲット オブジェクトの名前を登録します。</span><span class="sxs-lookup"><span data-stu-id="95e34-103">To animate with <xref:System.Windows.Media.Animation.Storyboard> in code, you must create a <xref:System.Windows.NameScope> and register the target objects' names with the element that owns that name scope.</span></span> <span data-ttu-id="95e34-104">次の例で、<xref:System.Windows.NameScope>に対して作成`myMainPanel`です。</span><span class="sxs-lookup"><span data-stu-id="95e34-104">In the following example, a <xref:System.Windows.NameScope> is created for `myMainPanel`.</span></span> <span data-ttu-id="95e34-105">2 つのボタン`button1`と`button2`パネル、および登録されている、名前に追加されます。</span><span class="sxs-lookup"><span data-stu-id="95e34-105">Two buttons, `button1` and `button2`, are added to the panel, and their names registered.</span></span> <span data-ttu-id="95e34-106">複数のアニメーションと<xref:System.Windows.Media.Animation.Storyboard>が作成されます。</span><span class="sxs-lookup"><span data-stu-id="95e34-106">Several animations and a <xref:System.Windows.Media.Animation.Storyboard> are created.</span></span> <span data-ttu-id="95e34-107">ストーリー ボードの<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>アニメーションを開始するメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="95e34-107">The storyboard's <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method is used to start the animations.</span></span>  
  
 <span data-ttu-id="95e34-108">`button1`、 `button2`、および`myMainPanel`すべて同じ名前のスコープを共有、それらのいずれかをと共に使用することができます、 <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>アニメーションを開始するメソッド。</span><span class="sxs-lookup"><span data-stu-id="95e34-108">Because `button1`, `button2`, and `myMainPanel` all share the same name scope, any one of them can be used with the <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method to start the animations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95e34-109">例</span><span class="sxs-lookup"><span data-stu-id="95e34-109">Example</span></span>  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="95e34-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="95e34-110">See Also</span></span>  
 [<span data-ttu-id="95e34-111">ストーリーボードを使ってプロパティをアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="95e34-111">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [<span data-ttu-id="95e34-112">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="95e34-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
