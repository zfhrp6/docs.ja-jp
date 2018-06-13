---
title: '方法 : Windows フォーム コントロールに属性を適用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: 49c2aaa48a48e33a71b5112db31991975011551d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529637"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>方法 : Windows フォーム コントロールに属性を適用する
デザイン環境と正しく通信してを実行時に正しく実行するコンポーネントとコントロールを開発するには、クラスとメンバーに属性を正しく適用する必要があります。  
  
## <a name="example"></a>例  
 次のコード例では、カスタム コントロールでいくつかの属性を使用する方法を示します。 コントロールでは、単純なログ記録機能を示します。 内のデータ ソースから送信された値が表示されます、コントロールがデータ ソースにバインドされている場合、<xref:System.Windows.Forms.DataGridView>コントロール。 値で指定された値を超えた場合、`Threshold`プロパティ、`ThresholdExceeded`イベントが発生します。  
  
 `AttributesDemoControl`を持つ値をログに記録、`LogEntry`クラスです。 `LogEntry`クラスは、テンプレート クラスは、ログを記録する型でパラメーター化されたことを意味します。 たとえば場合、`AttributesDemoControl`型のログ記録の値は、 `float`、各`LogEntry`インスタンスが宣言されているし、次のように使用します。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  `LogEntry`パラメーター化された任意の型によって、パラメーターの型を操作する、リフレクションを使用する必要があります、します。 パラメーターの型を使用するしきい値機能`T`実装する必要があります、<xref:System.IComparable>インターフェイスです。  
  
 ホストする、フォーム、`AttributesDemoControl`パフォーマンス カウンターを定期的に照会します。 内の各値はパッケージ化、`LogEntry`適切な型のフォームの追加と<xref:System.Windows.Forms.BindingSource>です。 `AttributesDemoControl` 、データ バインディングによって、値を受信し、内の値が表示されます、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 最初のコード例は、`AttributesDemoControl`実装します。 2 番目のコード例を使用するフォームを示しています、`AttributesDemoControl`です。  
  
## <a name="class-level-attributes"></a>クラス レベルの属性  
 いくつかの属性は、クラス レベルで適用されます。 次のコード例では、一般的に Windows フォーム コントロールに適用される属性を示します。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>TypeConverter 属性  
 <xref:System.ComponentModel.TypeConverterAttribute> 一般的に使用される別のクラス レベル属性です。 次のコード例の使用を示しています、`LogEntry`クラスです。 この例では、実装も示しています、<xref:System.ComponentModel.TypeConverter>の`LogEntry`と呼ばれる型`LogEntryTypeConverter`です。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>メンバー レベルの属性  
 いくつかの属性は、メンバー レベルで適用されます。 次のコード例では、一般的に Windows フォーム コントロールのプロパティに適用されるいくつかの属性を示します。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>AmbientValue 属性  
 次の例で、<xref:System.ComponentModel.AmbientValueAttribute>し、デザイン環境との相互作用をサポートするコードを示しています。 この操作が呼び出された*アンビエンス*です。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>データ バインド属性  
 次の例では、複合データ バインディングの実装を示します。 クラス レベル<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>表示されている、以前を指定します、`DataSource`と`DataMember`プロパティをデータ バインディングを使用します。 <xref:System.ComponentModel.AttributeProviderAttribute>の型を指定します、`DataSource`プロパティにバインドされます。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   ホストするフォーム、`AttributesDemoControl`への参照が必要です、`AttributesDemoControl`アセンブリを構築できるようにします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IComparable>  
 <xref:System.Windows.Forms.DataGridView>  
 [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Windows フォーム コントロールの属性](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 [方法: designerserializationvisibilityattribute を使用、標準的なデータ型のコレクションをシリアル化](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)
