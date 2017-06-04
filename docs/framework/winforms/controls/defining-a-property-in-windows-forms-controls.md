---
title: "Windows フォーム コントロールのプロパティの定義 | Microsoft Docs"
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
  - "カスタム コントロール [Windows フォーム], 定義 (プロパティをコードで)"
  - "プロパティ [Windows フォーム], 定義 (コードで)"
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Windows フォーム コントロールのプロパティの定義
プロパティの概要については、「[プロパティの概要](../Topic/Properties%20Overview.md)」を参照してください。  プロパティを定義する場合に考慮する必要がある点を次に示します。  
  
-   定義するプロパティに属性を適用する必要があります。  属性によって、デザイナーでのプロパティの表示形式が指定されます。  詳細については、「[コンポーネントのデザイン時属性](../Topic/Design-Time%20Attributes%20for%20Components.md)」を参照してください。  
  
-   プロパティの変更がコントロールのビジュアル表示に影響する場合は、`set` アクセサーから <xref:System.Windows.Forms.Control.Invalidate%2A> メソッド \(<xref:System.Windows.Forms.Control> から継承されたメソッド\) を呼び出します。  すると、<xref:System.Windows.Forms.Control.Invalidate%2A> によって、コントロールを再描画する <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドが呼び出されます。  効率的な点から、<xref:System.Windows.Forms.Control.Invalidate%2A> メソッドを複数回呼び出しても <xref:System.Windows.Forms.Control.OnPaint%2A> が呼び出されるのは 1 回だけです。  
  
-   .NET Framework クラス ライブラリには、整数、10 進数、ブール値などの一般的なデータ型のための型コンバーターが用意されています。  型コンバーターでは、一般に文字列を値へ変換する、つまり文字列データを他のデータ型に変換することが目的です。  標準的なデータ型は既定の型コンバーターに関連付けられています。既定の型コンバーターでは、値から文字列への変換と、文字列から適切なデータ型への変換が行われます。  カスタム \(非標準\) データ型のプロパティを定義する場合には、そのプロパティに関連付ける型コンバーターを指定する属性を適用する必要があります。  属性を使用して、カスタム UI 型エディターをプロパティに関連付けることもできます。  UI 型エディターには、プロパティやデータ型を編集するためのユーザー インターフェイスが備わっています。  カラー ピッカーは、UI 型エディターの例です。  属性の例については、このトピックの最後に示します。  
  
    > [!NOTE]
    >  カスタム プロパティを処理できる型コンバーターまたは UI 型エディターがない場合には、「[Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md)」の説明に従ってコンバーターまたはエディターを実装できます。  
  
 `FlashTrackBar` カスタム コントロールの `EndColor` というカスタム プロパティを定義するコード片を次に示します。  
  
```vb  
Public Class FlashTrackBar  
   Inherits Control  
   ...  
   ' Private data member that backs the EndColor property.  
   Private _endColor As Color = Color.LimeGreen  
  
   ' The Category attribute tells the designer to display  
   ' it in the Flash grouping.   
   ' The Description attribute provides a description of  
   ' the property.   
   <Category("Flash"), _  
   Description("The ending color of the bar.")>  _  
   Public Property EndColor() As Color  
      ' The public property EndColor accesses _endColor.  
      Get  
         Return _endColor  
      End Get  
      Set  
         _endColor = value  
         If Not (baseBackground Is Nothing) And showGradient Then  
            baseBackground.Dispose()  
            baseBackground = Nothing  
         End If  
         ' The Invalidate method calls the OnPaint method, which redraws    
         ' the control.  
         Invalidate()  
      End Set  
   End Property  
   ...  
End Class  
  
```  
  
```csharp  
public class FlashTrackBar : Control {  
   ...  
   // Private data member that backs the EndColor property.  
   private Color endColor = Color.LimeGreen;  
   // The Category attribute tells the designer to display  
   // it in the Flash grouping.   
   // The Description attribute provides a description of  
   // the property.   
   [  
   Category("Flash"),  
   Description("The ending color of the bar.")  
   ]  
   // The public property EndColor accesses endColor.  
   public Color EndColor {  
      get {  
         return endColor;  
      }  
      set {  
         endColor = value;  
         if (baseBackground != null && showGradient) {  
            baseBackground.Dispose();  
            baseBackground = null;  
         }  
         // The Invalidate method calls the OnPaint method, which redraws   
         // the control.  
         Invalidate();  
      }  
   }  
   ...  
}  
```  
  
 型コンバーターと UI 型エディターを `Value` プロパティに関連付けるコード片を次に示します。  このコードでは、`Value` プロパティが整数であり、このプロパティには既定の型コンバーターが設定されていますが、<xref:System.ComponentModel.TypeConverterAttribute> 属性によってカスタム型コンバーター \(`FlashTrackBarValueConverter`\) が適用されます。これにより、デザイナーではこの `Value` プロパティがパーセントとして表示されます。  `FlashTrackBarValueEditor` UI 型エディターを使用すると、パーセント値が視覚的に表示されます。  この例では、さらに <xref:System.ComponentModel.TypeConverterAttribute> 属性に指定された型コンバーターまたは <xref:System.ComponentModel.EditorAttribute> 属性に指定された型エディターが既定のコンバーターをオーバーライドします。  
  
```vb  
<Category("Flash"), _  
TypeConverter(GetType(FlashTrackBarValueConverter)), _  
Editor(GetType(FlashTrackBarValueEditor), _  
GetType(UITypeEditor)), _  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")>  _  
Public ReadOnly Property Value() As Integer  
...  
End Property  
  
```  
  
```csharp  
[  
Category("Flash"),   
TypeConverter(typeof(FlashTrackBarValueConverter)),  
Editor(typeof(FlashTrackBarValueEditor), typeof(UITypeEditor)),  
Description("The current value of the track bar.  You can enter an actual value or a percentage.")  
]  
public int Value {  
...  
}  
```  
  
## 参照  
 [Windows フォーム コントロールのプロパティ](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)   
 [ShouldSerialize メソッドと Reset メソッドによる既定値の定義](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)   
 [プロパティ変更イベント](../../../../docs/framework/winforms/controls/property-changed-events.md)   
 [Windows フォーム コントロールの属性](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)