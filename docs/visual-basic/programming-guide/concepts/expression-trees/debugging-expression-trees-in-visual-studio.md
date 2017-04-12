---
title: "Visual Studio (Visual Basic) で式ツリーのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: efbd8c19947c45b3ba15ce7b574000d56526ef45
ms.lasthandoff: 03/13/2017

---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Visual Studio (Visual Basic) で式ツリーのデバッグ
アプリケーションをデバッグするときは、構造と式ツリーの内容を分析できます。 式ツリー構造の簡単な概要を取得するには、使用することができます、`DebugView`プロパティで、デバッグ モードでのみ使用できます。 デバッグの詳細については、次を参照してください。 [Visual Studio でのデバッグ](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio)します。  
  
 式ツリーの内容をわかりやすく示した、`DebugView`プロパティは、Visual Studio ビジュアライザーを使用します。 詳細については、次を参照してください。[カスタム ビジュアライザーの作成](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)します。  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a>式ツリーのビジュアライザーを開く  
  
1.  横に表示される、虫眼鏡アイコンをクリックして、`DebugView`プロパティで、式ツリーの**データヒント**、**ウォッチ**ウィンドウで、 **[自動変数]**ウィンドウで、または**[ローカル]**ウィンドウです。  
  
     ビジュアライザーの一覧が表示されます。  
  
2.  使用するビジュアライザーをクリックします。  
  
 各式の型は、次のセクションで説明されているビジュアライザーに表示されます。  
  
## <a name="parameterexpressions"></a>ParameterExpressions  
 <xref:System.Linq.Expressions.ParameterExpression>変数名には、先頭に「$」記号が表示されます。</xref:System.Linq.Expressions.ParameterExpression>  
  
 パラメーターが名前を持たない場合、名前が割り当てられます、自動的に生成されたなど`$var1`または`$var2`です。  
  
### <a name="examples"></a>例  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer), "num")  
    ```  
  
     `DebugView` プロパティ  
  
     `$num`  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer))  
    ```  
  
     `DebugView` プロパティ  
  
     `$var1`  
  
## <a name="constantexpressions"></a>ConstantExpressions  
 <xref:System.Linq.Expressions.ConstantExpression>、文字列、整数値を表すオブジェクトと`null`定数の値が表示されます</xref:System.Linq.Expressions.ConstantExpression>。  
  
### <a name="examples"></a>例  
  
-   `Expression`  
  
    ```vb  
    Dim num as Integer= 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     `DebugView` プロパティ  
  
     10  
  
-   `Expression`  
  
    ```vb  
    Dim num As Double = 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     `DebugView` プロパティ  
  
     10 日  
  
## <a name="blockexpression"></a>BlockExpression  
 場合の種類、<xref:System.Linq.Expressions.BlockExpression>オブジェクトは、ブロックの最後の式の型とは異なるに、型を表示、`DebugInfo`山かっこでプロパティ (\<と >).</xref:System.Linq.Expressions.BlockExpression> それ以外の場合の種類、<xref:System.Linq.Expressions.BlockExpression>オブジェクトは表示されません</xref:System.Linq.Expressions.BlockExpression>。  
  
### <a name="examples"></a>例  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))  
    ```  
  
     `DebugView` プロパティ  
  
     `.Block() {`  
  
     `"test"`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression =   
    Expression.Block(GetType(Object), Expression.Constant("test"))  
    ```  
  
     `DebugView` プロパティ  
  
     `.Block<System.Object>() {`  
  
     `"test"`  
  
     `}`  
  
## <a name="lambdaexpression"></a>LambdaExpression  
 <xref:System.Linq.Expressions.LambdaExpression>オブジェクトは、デリゲート型と共に表示されます。</xref:System.Linq.Expressions.LambdaExpression>  
  
 ラムダ式が名を持たない場合、名前が割り当てられます、自動的に生成されたなど`#Lambda1`または`#Lambda2`です。  
  
### <a name="examples"></a>例  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))  
    ```  
  
     `DebugView` プロパティ  
  
     `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLamda", Nothing)  
    ```  
  
     `DebugView` プロパティ  
  
     `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
## <a name="labelexpression"></a>LabelExpression  
 既定値を指定する場合、<xref:System.Linq.Expressions.LabelExpression>オブジェクトの前にこの値が表示されて、<xref:System.Linq.Expressions.LabelTarget>オブジェクト</xref:System.Linq.Expressions.LabelTarget></xref:System.Linq.Expressions.LabelExpression>。  
  
 `.Label`トークンは、ラベルの先頭を指定します。 `.LabelTarget`トークンにジャンプ先のターゲットの送信先を示します。  
  
 ラベルが名前を持たない場合、名前が割り当てられます、自動的に生成されたなど`#Label1`または`#Label2`です。  
  
### <a name="examples"></a>例  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")  
    Dim label1 As BlockExpression = Expression.Block(  
    Expression.Goto(target, Expression.Constant(0)),  
    Expression.Label(target, Expression.Constant(-1)))  
    ```  
  
     `DebugView` プロパティ  
  
     `.Block() {`  
  
     `.Goto SampleLabel { 0 };`  
  
     `.Label`  
  
     `-1`  
  
     `.LabelTarget SampleLabel:`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label()  
    Dim block As BlockExpression = Expression.Block(  
    Expression.Goto(target), Expression.Label(target))  
    ```  
  
     `DebugView` プロパティ  
  
     `.Block() {`  
  
     `.Goto #Label1 { };`  
  
     `.Label`  
  
     `.LabelTarget #Label1:`  
  
     `}`  
  
## <a name="checked-operators"></a>Checked 演算子  
 Checked 演算子は、演算子の前に「#」記号が表示されます。 チェックされた加算演算子として表示するなどの`#+`です。  
  
### <a name="examples"></a>例  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.AddChecked(  
    Expression.Constant(1), Expression.Constant(2))  
    ```  
  
     `DebugView` プロパティ  
  
     `1 #+ 2`  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.ConvertChecked(  
    Expression.Constant(10.0), GetType(Integer))  
    ```  
  
     `DebugView` プロパティ  
  
     `#(System.Int32)10D`  
  
## <a name="see-also"></a>関連項目  
 [式ツリー (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)   
 [Visual Studio でのデバッグ](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio)   
 [カスタム ビジュアライザーを作成します。](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)
