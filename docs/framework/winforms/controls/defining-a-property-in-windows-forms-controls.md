---
title: Windows フォーム コントロールのプロパティの定義
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [Windows Forms], defining in code
- custom controls [Windows Forms], defining properties in code
ms.assetid: c2eb8277-a842-4d99-89a9-647b901a0434
ms.openlocfilehash: dc47d7152419d55b3e52aec70257e2b39e9aaca0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="defining-a-property-in-windows-forms-controls"></a>Windows フォーム コントロールのプロパティの定義
プロパティの概要については、「[プロパティの概要](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52)」を参照してください。 プロパティを定義するときには、いくつかの重要な考慮事項があります。  
  
-   定義するプロパティに属性を適用する必要があります。 属性によって、デザイナーでプロパティがどのように表示されるかが指定されます。 詳細については、「[コンポーネントのデザイン時属性](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)」を参照してください。  
  
-   プロパティを変更するコントロールのビジュアル表示に影響する場合、<xref:System.Windows.Forms.Control.Invalidate%2A>メソッド (コントロールの継承された<xref:System.Windows.Forms.Control>) から、`set`アクセサー。 <xref:System.Windows.Forms.Control.Invalidate%2A> さらに、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドで、コントロールを再描画します。 複数回呼び出す<xref:System.Windows.Forms.Control.Invalidate%2A>に 1 回の呼び出しと、<xref:System.Windows.Forms.Control.OnPaint%2A>効率を上げるのためです。  
  
-   .NET Framework クラス ライブラリでは、整数、10 進数、ブール値など、一般的なデータ型に対応する型コンバーターを使用できます。 型コンバーターは、一般に文字列から値への変換を行うために使用されます (文字列データから他のデータ型に変換)。 一般的なデータ型は、値を文字列に変換し、文字列を適切なデータ型に変換する既定の型コンバーターに関連付けられています。 カスタム (つまり、非標準的な) データ型であるプロパティを定義する場合、そのプロパティに関連付けられる型コンバーターを指定する属性を適用する必要があります。 また、属性を使用してカスタム UI 型エディターとプロパティを関連付けることもできます。 UI 型エディターには、プロパティやデータ型を編集するためのユーザー インターフェイスが備わっています。 たとえば、カラー ピッカーなどの UI 型エディターがあります。 属性の例は、このトピックの最後に記載されています。  
  
    > [!NOTE]
    >  型コンバーターまたは UI 型エディターをカスタム プロパティに使用できない場合、「[デザイン時サポートの拡張](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)」に示されているものを実装できます。  
  
 次のコード フラグメントは、カスタム コントロール `FlashTrackBar` に対して `EndColor` という名前のカスタム プロパティを定義します。  
  
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
  
 次のコード フラグメントは、型コンバーターと UI 型エディターをプロパティ `Value` に関連付けます。 ここでは`Value`整数であり、既定の型コンバーターですが、<xref:System.ComponentModel.TypeConverterAttribute>属性には、カスタム型コンバーターが適用されます (`FlashTrackBarValueConverter`) に対する比率として表示するデザイナーを有効にします。 UI 型エディター `FlashTrackBarValueEditor` により、そのパーセントを視覚的に表示できます。 この例も示しますを実行する型コンバーターまたはで指定されたエディター、<xref:System.ComponentModel.TypeConverterAttribute>または<xref:System.ComponentModel.EditorAttribute>属性が既定のコンバーターを上書きします。  
  
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
  
## <a name="see-also"></a>関連項目  
 [Windows フォーム コントロールのプロパティ](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [ShouldSerialize メソッドと Reset メソッドによる既定値の定義](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 [プロパティ変更イベント](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 [Windows フォーム コントロールの属性](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)
