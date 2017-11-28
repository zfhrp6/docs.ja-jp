---
title: "方法 : カーソルの種類を変更する"
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
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 41cd8c9cd647c7efbc4e6cf13517ed638245e51c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-change-the-cursor-type"></a>方法 : カーソルの種類を変更する
この例を変更する方法を示しています、<xref:System.Windows.Input.Cursor>とアプリケーションの特定の要素にマウス ポインターのです。  
  
 この例は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイルとファイルに隠れているコード。  
  
## <a name="example"></a>例  
 ユーザー インターフェイスを作成するから構成される、<xref:System.Windows.Controls.ComboBox>目的を選択する<xref:System.Windows.Input.Cursor>、1 組の<xref:System.Windows.Controls.RadioButton>カーソルの変更は 1 つの要素のみに適用されますか、アプリケーション全体に適用されるかを確認するオブジェクトと<xref:System.Windows.Controls.Border>これは、新しいカーソルに適用される要素です。  
  
 [!code-xaml[cursors#ChangeCursorsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 次のコードを作成、<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>カーソルの種類を変更したときに呼び出されるイベント ハンドラー、<xref:System.Windows.Controls.ComboBox>です。  Switch ステートメントがカーソルの名前とセットに基づくフィルター処理、<xref:System.Windows.FrameworkElement.Cursor%2A>プロパティを<xref:System.Windows.Controls.Border>6af159e2-19d6-4116-a30d-8f9a970621e5 *DisplayArea*です。  
  
 カーソルの変更は、"全体 Application"に設定されている場合、<xref:System.Windows.Input.Mouse.OverrideCursor%2A>プロパティに設定されている、<xref:System.Windows.FrameworkElement.Cursor%2A>のプロパティ、<xref:System.Windows.Controls.Border>コントロール。  これにより、アプリケーション全体を変更するカーソル。  
  
 [!code-csharp[cursors#ChangeCursorsSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a>関連項目  
 [入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)
