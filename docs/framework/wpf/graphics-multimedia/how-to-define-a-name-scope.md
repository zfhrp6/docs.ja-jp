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
ms.locfileid: "33559716"
---
# <a name="how-to-define-a-name-scope"></a>方法 : 名前のスコープを定義する
使用してアニメーション化<xref:System.Windows.Media.Animation.Storyboard>コードでは、作成する必要があります、<xref:System.Windows.NameScope>し、その名前のスコープを所有する要素を持つターゲット オブジェクトの名前を登録します。 次の例で、<xref:System.Windows.NameScope>に対して作成`myMainPanel`です。 2 つのボタン`button1`と`button2`パネル、および登録されている、名前に追加されます。 複数のアニメーションと<xref:System.Windows.Media.Animation.Storyboard>が作成されます。 ストーリー ボードの<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>アニメーションを開始するメソッドを使用します。  
  
 `button1`、 `button2`、および`myMainPanel`すべて同じ名前のスコープを共有、それらのいずれかをと共に使用することができます、 <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>アニメーションを開始するメソッド。  
  
## <a name="example"></a>例  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## <a name="see-also"></a>関連項目  
 [ストーリーボードを使ってプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
