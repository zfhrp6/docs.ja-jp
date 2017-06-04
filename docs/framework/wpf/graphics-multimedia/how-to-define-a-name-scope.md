---
title: "方法 : 名前のスコープを定義する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アニメーション, ストーリーボード, 手続き型コードでの"
  - "名前のスコープ, 定義"
  - "ストーリーボード, アニメーション化 (手続き型コードでの)"
ms.assetid: 4f361925-6a08-40dc-8231-a61111c6b28b
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : 名前のスコープを定義する
コードで <xref:System.Windows.Media.Animation.Storyboard> を使用してアニメーション化を行う場合は、<xref:System.Windows.NameScope> を作成し、その名前スコープを所有する要素にターゲット オブジェクトの名前を登録する必要があります。  次の例では、`myMainPanel` に対して <xref:System.Windows.NameScope> を作成します。  2 つのボタン `button1` と `button2` をパネルに追加し、その名前を登録します。  複数のアニメーションと <xref:System.Windows.Media.Animation.Storyboard> が作成されます。  アニメーションを開始するには、ストーリーボードの <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッドを使用します。  
  
 `button1`、`button2`、および `myMainPanel` はすべて同じ名前スコープを共有するため、いずれか 1 つを <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッドで使用して、アニメーションを開始できます。  
  
## 使用例  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## 参照  
 [ストーリーボードを使ってプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)