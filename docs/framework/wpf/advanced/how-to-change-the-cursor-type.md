---
title: "方法 : カーソルの種類を変更する | Microsoft Docs"
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
  - "カーソル (マウス ポインター)"
  - "マウス ポインター (カーソル), カーソルの種類"
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : カーソルの種類を変更する
特定の要素およびアプリケーションに対してマウス ポインターの <xref:System.Windows.Input.Cursor> を変更する方法を次の例に示します。  
  
 この例は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ファイルと分離コード ファイルで構成されています。  
  
## 使用例  
 この例で作成されるユーザー インターフェイスは、目的の <xref:System.Windows.Input.Cursor> を選択するための <xref:System.Windows.Controls.ComboBox>、カーソルの変更を単一の要素のみまたはアプリケーション全体のどちらに適用するかを決定する一組の <xref:System.Windows.Controls.RadioButton> オブジェクト、および新しいカーソルの適用対象の要素である <xref:System.Windows.Controls.Border> で構成されます。  
  
 [!code-xml[cursors#ChangeCursorsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 次の分離コードでは、<xref:System.Windows.Controls.ComboBox> でカーソルの種類を変更すると呼び出される <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> イベント ハンドラーを作成します。  switch ステートメントは、カーソル名でフィルター処理を行って、*DisplayArea* という名前の <xref:System.Windows.Controls.Border> の <xref:System.Windows.FrameworkElement.Cursor%2A> プロパティを設定します。  
  
 カーソルの変更の適用対象が "Entire Application \(アプリケーション全体\)" に設定されている場合は、<xref:System.Windows.Input.Mouse.OverrideCursor%2A> プロパティが、<xref:System.Windows.Controls.Border> コントロールの <xref:System.Windows.FrameworkElement.Cursor%2A> プロパティに設定されます。  これにより、カーソルの変更がアプリケーション全体に適用されます。  
  
 [!code-csharp[cursors#ChangeCursorsSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## 参照  
 [入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)