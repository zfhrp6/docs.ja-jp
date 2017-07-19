---
title: "方法 : Windows フォーム コントロールに属性を適用する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "属性 [Windows フォーム], 適用"
  - "コントロール [Windows フォーム], 適用 (属性を)"
  - "Windows フォーム コントロール, 適用 (属性を)"
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : Windows フォーム コントロールに属性を適用する
デザイン環境と適切に対話し、実行時に正しく実行されるコンポーネントやコントロールを開発するには、クラスとメンバーに属性を正しく適用する必要があります。  
  
## 使用例  
 次のコード例は、カスタム コントロールで属性を使用する方法を示しています。  このコントロールは、単純なログ記録機能を実行します。  このコントロールがデータ ソースにバインドされると、データ ソースから送られた値が <xref:System.Windows.Forms.DataGridView> コントロールに表示されます。  この値が、`Threshold` プロパティの指定値を超えている場合は、`ThresholdExceeded` イベントが生成されます。  
  
 `AttributesDemoControl` は、`LogEntry` クラスを使用して値のログを記録します。  `LogEntry` クラスはテンプレート クラスで、ログを記録する型でパラメーター化されます。  たとえば、`AttributesDemoControl` が `float` 型の値のログを記録する場合、各 `LogEntry` インスタンスを次のように宣言して使用します。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  `LogEntry` は、任意の型でパラメーター化されるため、パラメーター型で動作するためにリフレクションを使用する必要があります。  しきい値機能を使用するには、パラメーター型 `T` により、<xref:System.IComparable> インターフェイスを実装する必要があります。  
  
 `AttributesDemoControl` をホストするフォームは、パフォーマンス カウンターを定期的に照会します。  値はそれぞれ適切な型の `LogEntry` にパッケージ化され、フォームの <xref:System.Windows.Forms.BindingSource> に追加されます。  `AttributesDemoControl` は、データ バインディングを通じて値を受け取り、<xref:System.Windows.Forms.DataGridView> コントロールに表示します。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 最初のコード例は `AttributesDemoControl` の実装です。  2 番目のコード例は、`AttributesDemoControl` を使用するフォームを示しています。  
  
## クラス レベル属性  
 属性には、クラス レベルで適用されるものがあります。  Windows フォーム コントロールに一般的に適用される属性を次のコード例に示します。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### TypeConverter 属性  
 <xref:System.ComponentModel.TypeConverterAttribute> も一般的に使用されるクラス レベル属性です。  `LogEntry` クラスでのこの属性の使用方法を次のコード例に示します。  この例は、`LogEntryTypeConverter` と呼ばれる、`LogEntry` 型の <xref:System.ComponentModel.TypeConverter> の実装も示しています。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## メンバー レベル属性  
 属性には、メンバー レベルで適用されるものがあります。  Windows フォーム コントロールのプロパティに一般的に適用される属性を次のコード例に示します。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### AmbientValue 属性  
 次のコード例は、<xref:System.ComponentModel.AmbientValueAttribute> と、この属性とデザイン環境との対話をサポートするコードを示しています。  このような対話を*アンビエンス*と言います。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### データ バインディング属性  
 複合データ バインディングの実装例を次に示します。  前記のクラス レベル <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> で、データ バインディングで使用する `DataSource` プロパティと `DataMember` プロパティを指定します。  <xref:System.ComponentModel.AttributeProviderAttribute> で、`DataSource` プロパティをバインドする型を指定します。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## コードのコンパイル  
  
-   `AttributesDemoControl` をホストするフォームを作成するには、`AttributesDemoControl` アセンブリが必要です。  
  
## 参照  
 <xref:System.IComparable>   
 <xref:System.Windows.Forms.DataGridView>   
 [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [Windows フォーム コントロールの属性](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)   
 [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](../Topic/How%20to:%20Serialize%20Collections%20of%20Standard%20Types%20with%20the%20DesignerSerializationVisibilityAttribute.md)