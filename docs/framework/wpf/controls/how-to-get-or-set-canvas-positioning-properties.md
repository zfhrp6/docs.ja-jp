---
title: "方法 : Canvas の配置プロパティを取得または設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Canvas control [WPF], setting positioning properties
ms.assetid: 1636b950-2b5a-4507-8a10-c5034cc58b1c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2b01657088c388ad09037716278dc0788de2abb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-or-set-canvas-positioning-properties"></a>方法 : Canvas の配置プロパティを取得または設定する
この例の配置のメソッドを使用する方法を示しています、<xref:System.Windows.Controls.Canvas>要素に子コンテンツを配置します。 この例の内容を使用して、<xref:System.Windows.Controls.ListBoxItem>を表す位置指定値し、のインスタンスに値を変換します<xref:System.Double>、これは必須の引数の位置を決定します。 値は文字列に変換し、内のテキストとして表示されます、<xref:System.Windows.Controls.TextBlock>要素を使用して、<xref:System.Windows.Controls.Canvas.GetLeft%2A>メソッドです。  
  
## <a name="example"></a>例  
 次の例を作成、<xref:System.Windows.Controls.ListBox>を持つ 11 個の選択可能な要素<xref:System.Windows.Controls.ListBoxItem>要素。 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>イベント トリガー、`ChangeLeft`後続のコード ブロックを定義するカスタム メソッド。  
  
 各<xref:System.Windows.Controls.ListBoxItem>を表す、<xref:System.Double>は引数の 1 つの値を<xref:System.Windows.Controls.Canvas.SetLeft%2A>メソッドの<xref:System.Windows.Controls.Canvas>を受け入れます。 使用するために、<xref:System.Windows.Controls.ListBoxItem>のインスタンスを表す<xref:System.Double>、最初に変換する必要があります、<xref:System.Windows.Controls.ListBoxItem>を正しいデータ型。  
  
 [!code-xaml[CanvasPositioningProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml#1)]  
  
 ユーザーが変更されたとき、<xref:System.Windows.Controls.ListBox>を呼び出すの選択、`ChangeLeft`カスタム メソッド。 このメソッドは、<xref:System.Windows.Controls.ListBoxItem>を<xref:System.Windows.LengthConverter>に変換するオブジェクト、<xref:System.Windows.Controls.ContentControl.Content%2A>の<xref:System.Windows.Controls.ListBoxItem>のインスタンスに<xref:System.Double>(この値は既にに変換されたことを確認、<xref:System.String>を使用して、 <xref:System.Windows.Controls.Control.ToString%2A>メソッドの場合)。 この値に渡され、<xref:System.Windows.Controls.Canvas.SetLeft%2A>と<xref:System.Windows.Controls.Canvas.GetLeft%2A>のメソッド<xref:System.Windows.Controls.Canvas>の位置を変更するために、`text1`オブジェクト。  
  
 [!code-csharp[CanvasPositioningProperties#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml.cs#2)]
 [!code-vb[CanvasPositioningProperties#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasPositioningProperties/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.ListBoxItem>  
 <xref:System.Windows.LengthConverter>  
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)
