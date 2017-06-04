---
title: "方法 : メソッドにバインドする | Microsoft Docs"
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
  - "バインド, メソッド"
  - "クラス, ObjectDataProvider"
  - "データ バインディング, バインド (ObjectDataProvider を使用してメソッドに)"
  - "メソッド, バインド"
  - "ObjectDataProvider クラス"
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : メソッドにバインドする
<xref:System.Windows.Data.ObjectDataProvider> を使用してメソッドにバインドする方法の例を次に示します。  
  
## 使用例  
 この例では、`TemperatureScale` はメソッド `ConvertTemp` を持つクラスで、2 つのパラメーター \(1 つは `double` でもう 1 つは `enum` 型 `TempType)` を取得して、指定した値をある温度尺度から他の温度尺度へ変換します。  次の例では、<xref:System.Windows.Data.ObjectDataProvider> を使用して `TemperatureScale` オブジェクトをインスタンス化します。  `ConvertTemp` メソッドは、2 つの指定したパラメーターで呼び出します。  
  
 [!code-xml[BindToMethod#WindowResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 このメソッドはリソースとして使用可能となり、その結果にバインドできます。  次の例では、<xref:System.Windows.Controls.TextBox> の <xref:System.Windows.Controls.TextBox.Text%2A> プロパティと <xref:System.Windows.Controls.ComboBox> の <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> をこのメソッドの 2 つのパラメーターにバインドします。  これにより、ユーザーは、変換する温度と変換前の温度尺度を指定できます。  <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> が `true` に設定されることに注意してください。これは、<xref:System.Windows.Data.ObjectDataProvider> \(`TemperatureScale` オブジェクト\) によってラップされたオブジェクトのプロパティではなく、<xref:System.Windows.Data.ObjectDataProvider> インスタンスの <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> プロパティにバインドするためです。  
  
 最後の <xref:System.Windows.Controls.Label> の <xref:System.Windows.Controls.ContentControl.Content%2A> は、ユーザーが <xref:System.Windows.Controls.TextBox> の内容、または <xref:System.Windows.Controls.ComboBox> の選択を変更したときに更新されます。  
  
 [!code-xml[BindToMethod#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 コンバーター `DoubleToString` は、<xref:System.Windows.Data.IValueConverter.Convert%2A> 方向では double を受け取って string に変換し \([バインディング ソース](GTMT)から[バインディング ターゲット](GTMT)である <xref:System.Windows.Controls.TextBox.Text%2A> プロパティへ\)、<xref:System.Windows.Data.IValueConverter.ConvertBack%2A> 方向では `string` を `double` に変換します。  
  
 `InvalidationCharacterRule` は無効な文字をチェックする <xref:System.Windows.Controls.ValidationRule> です。  入力値が double 型の値でない場合は、既定のエラー テンプレート \(<xref:System.Windows.Controls.TextBox> の周囲の赤い境界線\) がユーザーへの通知として表示されます。  
  
## 参照  
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)   
 [列挙値にバインドする](../../../../docs/framework/wpf/data/how-to-bind-to-an-enumeration.md)