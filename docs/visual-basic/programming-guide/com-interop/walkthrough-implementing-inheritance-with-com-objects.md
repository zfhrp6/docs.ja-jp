---
title: "チュートリアル: COM オブジェクト (Visual Basic) での継承を実装する |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- inheritance, COM reusability
- base classes, COM reusability
- inheritance, walkthroughs
- derived classes, COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fa7753847619f14600c924cba01e55651c4f17c2
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>チュートリアル: COM オブジェクトによる継承の実装 (Visual Basic)
Visual Basic クラスを派生する`Public`でもの以前のバージョンで作成された COM オブジェクトのクラス[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。 プロパティと COM オブジェクトから継承されたクラスのメソッドをオーバーライドまたはプロパティと同じようにオーバー ロード、およびその他の基本クラスのメソッドをオーバーライドまたはオーバー ロードします。 COM オブジェクトからの継承は、再コンパイルしない既存のクラス ライブラリがある場合に便利です。  
  
 次の手順では、Visual Basic 6.0 を使用して、クラスが含まれている COM オブジェクトを作成し、基本クラスとして使用する方法を示します。  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>このチュートリアルで使用される COM オブジェクトを構築するには  
  
1.  Visual Basic 6.0 では、新しい ActiveX DLL プロジェクトを開きます。 という名前のプロジェクト`Project1`が作成されます。 という名前のクラスがある`Class1`です。  
  
2.  **プロジェクト エクスプ ローラー**を右クリックして**Project1**、クリックして**Project1 プロパティ**します。 **プロジェクトのプロパティ** ダイアログ ボックスが表示されます。  
  
3.  **全般**のタブ、**プロジェクトのプロパティ** ダイアログ ボックスで、」と入力して、プロジェクト名を変更`ComObject1`で、**プロジェクト名**フィールドです。  
  
4.  **プロジェクト エクスプ ローラー**を右クリックして`Class1`、クリックして**プロパティ**します。 **プロパティ**クラスのウィンドウが表示されます。  
  
5.  変更、`Name`プロパティを`MathFunctions`します。  
  
6.  **プロジェクト エクスプ ローラー**を右クリックして`MathFunctions`、クリックして**コードの表示**します。 **コード エディター**が表示されます。  
  
7.  プロパティ値を保持するローカル変数を追加します。  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  プロパティを追加`Let`とプロパティ`Get`プロパティ プロシージャ。  
  
    ```  
    Public Property Let Prop1(ByVal vData As Integer)  
       'Used when assigning a value to the property.  
       mvarProp1 = vData  
    End Property  
    Public Property Get Prop1() As Integer  
       'Used when retrieving a property's value.  
       Prop1 = mvarProp1  
    End Property  
    ```  
  
9. 関数を追加します。  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. 作成しをクリックして、COM オブジェクトを登録**、ComObject1.dll**上、**ファイル**メニュー。  
  
    > [!NOTE]
    >  作成したクラスを公開することもできます。 ただし[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]COM オブジェクトとして、真の COM オブジェクトではありませんし、このチュートリアルでは使用できません。 詳細については、「 [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)します。  
  
## <a name="interop-assemblies"></a>相互運用機能アセンブリ  
 次の手順では、COM オブジェクト) などのアンマネージ コードとマネージ コード間のブリッジとして機能する相互運用機能アセンブリを作成します[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]を使用します。 相互運用機能アセンブリを[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]などの COM の使用の詳細の多くのオブジェクトのハンドルが作成*相互運用マーシャ リング*、パッケージ パラメーターと戻り値を等価のデータの処理と COM オブジェクトの間で移動するための型します。 内の参照、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]実際の COM オブジェクトではなく、相互運用機能アセンブリをアプリケーションのポイント。  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>Visual Basic 2005 およびそれ以降のバージョンで、COM オブジェクトを使用するには  
  
1.  新しい[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Windows アプリケーション プロジェクト。  
  
2.  **プロジェクト** メニューのをクリックして**参照の追加**します。  
  
     **参照の追加** ダイアログ ボックスが表示されます。  
  
3.  **COM**  タブをダブルクリックして`ComObject1`で、**コンポーネント名**を一覧表示し、クリックして**ok**します。  
  
4.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。  
  
     **新しい項目の追加** ダイアログ ボックスが表示されます。  
  
5.  **テンプレート** ウィンドウで、をクリックして**クラス**します。  
  
     既定のファイル名`Class1.vb`に表示されます、**名前**フィールドです。 このフィールドは変更をクリックして MathClass.vb**追加**します。 という名前のクラスを作成この`MathClass`、し、そのコードを表示します。  
  
6.  先頭に次のコードを追加`MathClass`COM クラスから継承します。  
  
     [!code-vb[VbVbalrInterop #&31;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]  
  
7.  次のコードを追加することで、基本クラスのパブリック メソッドをオーバー ロード`MathClass`:  
  
     [!code-vb[VbVbalrInterop&#32;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]  
  
8.  次のコードを追加することで、継承されたクラスを拡張`MathClass`:  
  
     [!code-vb[VbVbalrInterop #&33;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]  
  
 新しいクラスは、COM オブジェクトの基本クラスのプロパティを継承し、メソッドをオーバー ロード、クラスを拡張する新しいメソッドを定義します。  
  
#### <a name="to-test-the-inherited-class"></a>継承されたクラスをテストするには  
  
1.  スタートアップ フォームにボタンを追加し、そのコードを表示することをダブルクリックします。  
  
2.  ボタンの`Click`イベント ハンドラーのプロシージャのインスタンスを作成するには、次のコードを追加`MathClass`オーバー ロードされたメソッドを呼び出します。  
  
     [!code-vb[VbVbalrInterop #&34;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]  
  
3.  F5 キーを押して、プロジェクトを実行します。  
  
 フォーム上のボタンをクリックすると、`AddNumbers`メソッドが呼び出された最初`Short`データ型の数字、および[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]基本クラスから適切な方法を選択します。 2 番目の呼び出し`AddNumbers`からメソッドをオーバー ロードに転送`MathClass`します。 3 番目の呼び出しを呼び出して、`SubtractNumbers`メソッドで、クラスを拡張します。 基本クラスのプロパティを設定すると、され、値が表示されます。  
  
## <a name="next-steps"></a>次の手順  
 気付いたかもしれませんが、オーバー ロードされた`AddNumbers`して、データ型、COM オブジェクトの基本クラスから継承されたメソッドと同じ関数が表示されます。 これは、引数および基本クラスのメソッドのパラメーターが Visual Basic 6.0 での 16 ビット整数値として定義されている型の 16 ビット整数として公開されるため`Short`Visual Basic のそれ以降のバージョン。 新しい関数は、32 ビットの整数入力し、基本クラスの関数をオーバー ロードします。  
  
 COM オブジェクトを使用する場合は、パラメーターのサイズとデータ型を確認することを確認します。 たとえば、Visual Basic 6.0 コレクション オブジェクトを引数として受け取り、COM オブジェクトを使用しているときに、それ以降のバージョンの Visual Basic からコレクションを提供できません。  
  
 プロパティとメソッドが COM クラスから継承されたオーバーライドできます、つまり、ローカルのプロパティまたはプロパティを置換するメソッドまたは COM の基本クラスから継承されたメソッドを宣言することができます。 COM の継承されたプロパティをオーバーライドするためのルールは、その他のプロパティと、次の例外のメソッドをオーバーライドするための規則に似ています。  
  
-   任意のプロパティまたは COM クラスから継承されたメソッドをオーバーライドする場合は、その他のすべての継承されたプロパティとメソッドをオーバーライドする必要があります。  
  
-   使用するプロパティ`ByRef`パラメーターはオーバーライドできません。  
  
## <a name="see-also"></a>関連項目  
 [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)   
 [Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Short データ型](../../../visual-basic/language-reference/data-types/short-data-type.md)
