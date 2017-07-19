---
title: "カスタム コントロールへのメソッドの実装 | Microsoft Docs"
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
  - "メソッドの実装のユーザー コントロール [Windows フォーム]"
  - "メソッドのオーバー ロードのカスタム コントロール [Windows フォーム]"
  - "カスタム コントロール [Windows フォーム] メソッドの実装"
  - "メソッド [Windows フォーム]"
  - "カスタム コントロールのメソッド [Windows フォーム]"
ms.assetid: 35d14fca-4bb4-4a27-8211-1f7a98ea27de
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# カスタム コントロールへのメソッドの実装
コントロールにメソッドを実装する方法は、他のコンポーネントにメソッドが実装する場合と同じです。  
  
 Visual Basic では、値を返す必要のあるメソッドは `Public Function` として実装されます。 値が返されない場合は、`Public Sub` として実装されます。 メソッドは次の構文で宣言します。  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 関数は値を返すため、整数、文字列、オブジェクトなど、戻り値の型を指定する必要があります。 `Function` プロシージャや `Sub` プロシージャが引数をとる場合は、引数も指定する必要があります。  
  
 Visual Basic とは異なり、C# では関数とプロシージャが区別されません。 メソッドは値を返すか、または `void` を返します。 C# のパブリック メソッドを宣言する構文は次のとおりです。  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 メソッドを宣言する際、可能な限り、メソッドのすべての引数を明示的なデータ型として宣言します。 オブジェクト参照を使用する引数は、特定のクラス型として宣言される必要があります (例: `As Widget` ではなく、`As Object`)。 Visual Basic では、既定の設定 `Option Strict` によって自動的にこの規則が適用されます。  
  
 型付き引数を使用することにより、開発者によるエラーの多くを、実行時ではなく、コンパイラによって検出できます。 コンパイラは常に多くのエラーを検出するのに対し、ランタイム テストは、テスト スイートと同程度の精度しかありません。  
  
## <a name="overloaded-methods"></a>オーバーロードされたメソッド  
 コントロールのユーザーが、メソッドにさまざまなパラメーターの組み合わせを指定できるようにするには、明示的なデータ型を使用して、メソッドのオーバーロードを複数提供します。 テスト時にエラーが検出されない場合があるため、任意のデータ型を含めることのできる `As Object` として宣言するパラメーターは作成しないでください。  
  
> [!NOTE]
>  共通言語ランタイムの汎用データ型は、`Object` ではなく、`Variant` です。 `Variant` は、言語から削除されました。  
  
 たとえば、`Spin` という仮想のコントロールに `Widget` メソッドがあり、スピンの方向と速度を直接指定するか、角運動量を吸収する他の `Widget` オブジェクトを指定できます。  
  
```vb  
Overloads Public Sub Spin( _  
   ByVal SpinDirection As SpinDirectionsEnum, _  
   ByVal RevolutionsPerSecond As Double)  
   ' Implementation code here.  
End Sub  
Overloads Public Sub Spin(ByVal Driver As Widget) _  
   ' Implementation code here.  
End Sub  
```  
  
```csharp  
public void Spin(SpinDirectionsEnum spinDirection, double revolutionsPerSecond)  
{  
   // Implementation code here.  
}  
  
public void Spin(Widget driver)  
{  
   // Implementation code here.  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [イベント](../../../../docs/standard/events/index.md)   
 [Windows フォーム コントロールのプロパティ](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)