---
title: "Visual Studio (Visual Basic) でオブジェクトを永続化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- VB
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0ff6320aee65850b8b445f445f80b4bbe2c9c254
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a>チュートリアル: Visual Studio (Visual Basic) でオブジェクトを永続化
既定値にオブジェクトのプロパティを設定するにはデザイン時に、実行時に入力した値は、オブジェクトが破棄されるときに失われます。 シリアル化を使用して、値を格納し、次回のオブジェクトをインスタンス化して取得することにより、インスタンス間でオブジェクトのデータを永続化できます。  
  
> [!NOTE]
>  Visual basic で名前または番号などの単純なデータを格納することができますを使用して、`My.Settings`オブジェクトです。 詳細については、次を参照してください。 [My.settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)します。  
  
 このチュートリアルでは、単純なを作成します`Loan`オブジェクトし、そのデータ ファイルを保持します。 その後、オブジェクトの再作成するときに、データをファイルから取得されます。  
  
> [!IMPORTANT]
>  次のコード例では、ファイルが存在しない場合は新規にファイルを作成します。 そのアプリケーションにする必要がありますが、ファイルを作成する必要がある場合、`Create`フォルダーのアクセスを許可します。 権限は、アクセス制御リストを使用して設定されます。 アプリケーションにのみ必要な場合は、ファイルが既に存在する`Write`アクセス許可、いずれか小さいほうのアクセスを許可します。 展開時に、ファイルを作成し、だけを許可する方が安全では可能であれば、 `Read` (フォルダーに対する作成アクセス許可) ではなく&1; つのファイルへのアクセス許可。 また、ルート フォルダーまたは Program Files フォルダーよりもユーザー フォルダーにデータを書き込む方が安全です。  
  
> [!IMPORTANT]
>  この例では、バイナリのデータを格納します。 これらの形式は、パスワードやクレジット_カード番号などの機密データの指定しないでください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="creating-the-loan-object"></a>ローン オブジェクトを作成します。  
 作成するには、まず、`Loan`クラスおよびクラスを使用するテスト アプリケーションです。  
  
### <a name="to-create-the-loan-class"></a>ローン クラスを作成するには  
  
1.  新しいクラス ライブラリ プロジェクトを作成し、"LoanClass"という名前を付けます。 詳細については、「[ソリューションとプロジェクトの作成](http://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects)」を参照してください。  
  
2.  **ソリューション エクスプ ローラー**Class1 ファイルのショートカット メニューを開き、選択**の名前を変更**します。 ファイルを`Loan`ENTER キーを押します。 ファイルの名前変更の名前も変更は、クラスに`Loan`します。  
  
3.  クラスに次のパブリック メンバーを追加します。  
  
    ```vb  
    Public Class Loan  
        Implements System.ComponentModel.INotifyPropertyChanged  
  
        Public Property LoanAmount As Double  
        Public Property InterestRate As Double  
        Public Property Term As Integer  
  
        Private p_Customer As String  
        Public Property Customer As String  
            Get  
                Return p_Customer  
            End Get  
            Set(ByVal value As String)  
                p_Customer = value  
                RaiseEvent PropertyChanged(Me,  
                  New System.ComponentModel.PropertyChangedEventArgs("Customer"))  
            End Set  
        End Property  
  
        Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
          Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
  
        Public Sub New(ByVal loanAmount As Double,  
                       ByVal interestRate As Double,  
                       ByVal term As Integer,  
                       ByVal customer As String)  
  
            Me.LoanAmount = loanAmount  
            Me.InterestRate = interestRate  
            Me.Term = term  
            p_Customer = customer  
        End Sub  
    End Class  
    ```  
  
 使用する単純なアプリケーションを作成する必要があります、`Loan`クラスです。  
  
### <a name="to-create-a-test-application"></a>テスト アプリケーションを作成するには  
  
1.  ソリューションに Windows フォーム アプリケーション プロジェクトを追加する、**ファイル**] メニューの [選択**追加**、**新しいプロジェクト**します。  
  
2.  **新しいプロジェクトの追加** ダイアログ ボックスで、選択**Windows フォーム アプリケーション**、入力と`LoanApp`クリックして、プロジェクトの名前として**ok**  ダイアログ ボックスを閉じます。  
  
3.  **ソリューション エクスプ ローラー**、プロジェクトを選択します。  
  
4.  **プロジェクト**] メニューの [選択**スタートアップ プロジェクトとして設定**します。  
  
5.  **[プロジェクト]** メニューの **[参照の追加]**をクリックします。  
  
6.  **参照の追加** ダイアログ ボックスで、選択、**プロジェクト**タブし、LoanClass プロジェクトを選択します。  
  
7.  [OK **** ] をクリックしてダイアログ ボックスを閉じます。  
  
8.  デザイナーで、4 つの追加<xref:System.Windows.Forms.TextBox>フォームのコントロール</xref:System.Windows.Forms.TextBox>。  
  
9. コード エディターで、次のコードを追加します。  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. イベント ハンドラーを追加、`PropertyChanged`次のコードを使用してフォームに、イベント。  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 この時点では、ビルドおよびアプリケーションを実行することができます。 既定値を`Loan`クラスは、テキスト ボックスに表示されます。 7.5 から 7.1 に利率の値を変更して、アプリケーションを終了し、もう一度実行しようとしています。-値 7.5 の既定値に戻ります。  
  
 現実の世界での金利を変更する、定期的に、必ずしもアプリケーションを実行するたびにします。 アプリケーションを実行するたびに利率を更新するユーザーを作成するには、代わりのアプリケーション インスタンス間で最新の金利を保持することをお勧めします。 次の手順でを実行したローン クラスをシリアル化を追加することで。  
  
## <a name="using-serialization-to-persist-the-object"></a>シリアル化を使用して、オブジェクトを永続化  
 Loan クラスの値を保持するためを使用してクラスをマークする必要があります最初、`Serializable`属性です。  
  
### <a name="to-mark-a-class-as-serializable"></a>クラスをシリアル化可能としてマークするには  
  
-   ローン クラスのクラス宣言を次のように変更します。  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 `Serializable`属性は、ファイルに保存する、クラス内のすべてをコンパイラに指示します。 `PropertyChanged`イベントが Windows フォーム オブジェクトによって処理される、シリアル化することはできません。 `NonSerialized`を永続化しないクラス メンバーをマークする属性を使用できます。  
  
### <a name="to-prevent-a-member-from-being-serialized"></a>メンバーがシリアル化されないようにするには  
  
-   宣言を変更する、`PropertyChanged`次のように、イベント。  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 次の手順では、LoanApp アプリケーションにシリアル化コードを追加します。 クラスをシリアル化し、ファイルへの書き込みをするには、使用して、<xref:System.IO>と<xref:System.Xml.Serialization>名前空間</xref:System.Xml.Serialization></xref:System.IO>。 完全修飾名の入力を回避するのには、必要なクラス ライブラリへの参照を追加できます。  
  
### <a name="to-add-references-to-namespaces"></a>名前空間への参照を追加するには  
  
-   先頭に次のステートメントを追加、`Form1`クラス。  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     この場合、オブジェクトをバイナリ形式で保存するには、バイナリ フォーマッタを使用しています。  
  
 次の手順では、オブジェクトの作成時に、ファイルからオブジェクトを逆シリアル化するコードを追加します。  
  
### <a name="to-deserialize-an-object"></a>オブジェクトを逆シリアル化するには  
  
1.  シリアル化されたデータのファイル名をクラスには、定数を追加します。  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2.  コードの変更、`Form1_Load`次のように、イベント プロシージャ。  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        If File.Exists(FileName) Then  
            Dim TestFileStream As Stream = File.OpenRead(FileName)  
            Dim deserializer As New BinaryFormatter  
            TestLoan = CType(deserializer.Deserialize(TestFileStream), LoanClass.Loan)  
            TestFileStream.Close()  
        End If  
  
        AddHandler TestLoan.PropertyChanged, AddressOf Me.CustomerPropertyChanged  
  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
     まず必要がありますを確認するファイルが存在することに注意してください。 存在する場合は、作成、<xref:System.IO.Stream>バイナリ ファイルを読み取るためのクラスと<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>ファイルを変換するクラス</xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></xref:System.IO.Stream>。 また、ストリーム型からローン オブジェクトの種類に変換する必要があります。  
  
 次に、テキスト ボックスに入力されたデータを保存するコードを追加する必要があります、`Loan`クラス、および、ファイルにクラスをシリアル化する必要があります。  
  
### <a name="to-save-the-data-and-serialize-the-class"></a>データを保存し、クラスをシリアル化するには  
  
-   次のコードを追加、`Form1_FormClosing`イベント プロシージャ。  
  
    ```vb  
    Private Sub Form1_FormClosing() Handles MyBase.FormClosing  
        TestLoan.LoanAmount = CDbl(TextBox1.Text)  
        TestLoan.InterestRate = CDbl(TextBox2.Text)  
        TestLoan.Term = CInt(TextBox3.Text)  
        TestLoan.Customer = TextBox4.Text  
  
        Dim TestFileStream As Stream = File.Create(FileName)  
        Dim serializer As New BinaryFormatter  
        serializer.Serialize(TestFileStream, TestLoan)  
        TestFileStream.Close()  
    End Sub  
    ```  
  
 この時点では、もう一度ビルドして実行するアプリケーション。 最初に、既定値は、テキスト ボックスに表示されます。 値を変更し、4 つ目のテキスト ボックスに名前を入力しようとします。 アプリケーションを終了して再度実行します。 新しい値がテキスト ボックスに表示されていることに注意してください。  
  
## <a name="see-also"></a>関連項目  
 [シリアル化 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)   
 [Visual Basic のプログラミング ガイド](../../../../visual-basic/programming-guide/index.md)
