---
title: 'チュートリアル: COM オブジェクトによる継承の実装 (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: a1c1b7c247d3277c6614a4774395650c4c069c2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>チュートリアル: COM オブジェクトによる継承の実装 (Visual Basic)
Visual Basic クラスを派生させることができます`Public`も以前のバージョンの Visual Basic で作成された COM オブジェクトのクラスです。 プロパティと COM オブジェクトから継承されたクラスのメソッドをオーバーライドまたはプロパティと同様にオーバー ロード、およびその他の任意の基本クラスのメソッドをオーバーライドまたはオーバー ロードできます。 COM オブジェクトからの継承は、再コンパイルしたくない既存のクラス ライブラリがある場合に便利です。  
  
 次の手順では、Visual Basic 6.0 を使用して、クラスが含まれている COM オブジェクトを作成し、基底クラスとして使用する方法を示します。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>このチュートリアルで使用されている COM オブジェクトを構築するには  
  
1.  Visual Basic 6.0 では、新しい ActiveX DLL プロジェクトを開きます。 という名前のプロジェクト`Project1`を作成します。 という名前のクラスがある`Class1`です。  
  
2.  **プロジェクト エクスプ ローラー**を右クリックして**Project1**、クリックして**Project1 プロパティ**です。 **プロジェクト プロパティ** ダイアログ ボックスが表示されます。  
  
3.  **全般**のタブ、**プロジェクトのプロパティ** ダイアログ ボックスで、プロジェクトの名前を入力して変更`ComObject1`で、**プロジェクト名**フィールドです。  
  
4.  **プロジェクト エクスプ ローラー**を右クリックして`Class1`、クリックして**プロパティ**です。 **プロパティ**クラスのウィンドウが表示されます。  
  
5.  変更、`Name`プロパティを`MathFunctions`です。  
  
6.  **プロジェクト エクスプ ローラー**を右クリックして`MathFunctions`、クリックして**コードの表示**です。 **コード エディター**が表示されます。  
  
7.  プロパティの値を保持するローカル変数を追加します。  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  プロパティを追加`Let`およびプロパティ`Get`プロパティ プロシージャ。  
  
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
  
9. 関数を追加するには。  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. 作成しをクリックして、COM オブジェクトを登録**ように ComObject1.dll**上、**ファイル**メニュー。  
  
    > [!NOTE]
    >  COM オブジェクトとして Visual Basic で作成したクラスを公開することが true COM オブジェクトではないと、このチュートリアルでは使用できません。 詳細については、「 [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)です。  
  
## <a name="interop-assemblies"></a>相互運用機能アセンブリ  
 次の手順では、アンマネージ コード (COM オブジェクトなど) および Visual Studio を使用してマネージ コード間の仲介役として機能する、相互運用機能アセンブリを作成します。 Visual Basic によって作成される相互運用機能アセンブリでは、ように、COM オブジェクトの操作の詳細を処理*相互運用マーシャ リング*、パッケージ パラメーターと戻り値を等価のデータの処理の種類に移動してCOM オブジェクトです。 Visual Basic アプリケーション内の参照は、実際の COM オブジェクトではなく、相互運用機能アセンブリを指します。  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>Visual Basic 2005 およびそれ以降のバージョンで COM オブジェクトを使用するには  
  
1.  新しい Visual Basic Windows アプリケーション プロジェクトを開きます。  
  
2.  **[プロジェクト]** メニューの **[参照の追加]** をクリックします。  
  
     **[参照の追加]** ダイアログ ボックスが表示されます。  
  
3.  **COM**  タブをダブルクリックして`ComObject1`で、**コンポーネント名**を一覧表示し、をクリックして**OK**です。  
  
4.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。  
  
     **[新しい項目の追加]** ダイアログ ボックスが表示されます。  
  
5.  **テンプレート** ウィンドウで、をクリックして**クラス**です。  
  
     既定のファイル名、`Class1.vb`に表示されます、**名前**フィールドです。 このフィールドは MathClass.vb をクリックして変更**追加**です。 これがという名前のクラスを作成`MathClass`、し、そのコードを表示します。  
  
6.  先頭に次のコードを追加`MathClass`COM クラスから継承します。  
  
     [!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]  
  
7.  次のコードを追加することで、基本クラスのパブリック メソッドをオーバー ロード`MathClass`:  
  
     [!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]  
  
8.  次のコードを追加することで、継承されたクラスを拡張`MathClass`:  
  
     [!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]  
  
 新しいクラス、COM オブジェクトの基本クラスのプロパティを継承するには、メソッドをオーバー ロードおよびクラスを拡張する新しいメソッドを定義します。  
  
#### <a name="to-test-the-inherited-class"></a>継承されたクラスをテストするには  
  
1.  スタートアップ フォームにボタンを追加しをダブルクリックすると、そのコードを表示します。  
  
2.  ボタンの`Click`イベント ハンドラーのプロシージャのインスタンスを作成する次のコードを追加`MathClass`オーバー ロードされたメソッドを呼び出します。  
  
     [!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]  
  
3.  F5 キーを押してプロジェクトを実行します。  
  
 フォーム上のボタンをクリックすると、`AddNumbers`メソッドが呼び出された最初`Short`データ型の数値、Visual Basic は、基本クラスから、適切なメソッドを選択します。 2 番目の呼び出し`AddNumbers`からは、オーバー ロード メソッドに送られます`MathClass`です。 3 番目の呼び出しの呼び出し、`SubtractNumbers`メソッドで、クラスを拡張します。 基本クラスのプロパティが設定され、値が表示されます。  
  
## <a name="next-steps"></a>次の手順  
 お気付きをオーバー ロードされた`AddNumbers`と同じデータ型、COM オブジェクトの基本クラスから継承されたメソッドに関数が表示されます。 これは、引数と、基底クラス メソッドのパラメーターは、Visual Basic 6.0 の 16 ビット整数値として定義されますが、型の 16 ビット整数として公開されるため`Short`Visual Basic のそれ以降のバージョン。 新しい関数では、32 ビット整数値を受け入れるし、基本クラスの関数をオーバー ロードします。  
  
 COM オブジェクトを使用する場合は、パラメーターのサイズとデータ型を確認することを確認します。 たとえば、Visual Basic 6.0 コレクション オブジェクトを引数として受け取りを COM オブジェクトを使用しているときに、以降のバージョンの Visual Basic からコレクションを提供できません。  
  
 プロパティとメソッドが COM クラスから継承したオーバーライドできます、つまり、ローカル プロパティまたはプロパティを置換するメソッドまたは COM の基本クラスから継承されたメソッドを宣言することができます。 継承された COM プロパティをオーバーライドするため規則は、他のプロパティと、次の例外を持つメソッドをオーバーライドするための規則に似ています。  
  
-   任意のプロパティや、COM クラスから継承されたメソッドをオーバーライドする場合は、その他のすべての継承されたプロパティとメソッドをオーバーライドする必要があります。  
  
-   使用するプロパティ`ByRef`パラメーターをオーバーライドすることはできません。  
  
## <a name="see-also"></a>関連項目  
 [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Short データ型](../../../visual-basic/language-reference/data-types/short-data-type.md)
