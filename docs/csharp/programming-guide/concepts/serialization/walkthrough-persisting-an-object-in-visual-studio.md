---
title: "チュートリアル: オブジェクトの永続化 (Visual Studio) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
ms.assetid: a544ce46-ee25-49da-afd4-457a3d59bf63
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b1a3fc377875ee25baa0718a25b5ac509822154
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-c"></a>チュートリアル: オブジェクトの永続化 (Visual Studio) (C#)
オブジェクトのプロパティはデザイン時に既定値に設定できますが、そのオブジェクトが破棄されると、実行時に入力した値はすべて失われます。 シリアル化によってインスタンス間でオブジェクトのデータを永続化すると、値を保存しておき、次にそのオブジェクトをインスタンス化するときに、その値を取得することができます。  
  
 このチュートリアルでは、簡単な `Loan` オブジェクトを作成し、そのデータをファイルに永続化します。 その後、オブジェクトを再作成するときに、そのファイルからデータを取得します。  
  
> [!IMPORTANT]
>  次の例では、ファイルが存在しない場合は、新しいファイルが作成されます。 アプリケーションでファイルを作成する必要がある場合、そのアプリケーションには、フォルダーに対する `Create` アクセス許可が必要です。 アクセス許可は、アクセス制御リストを使用して設定します。 ファイルが既に存在する場合、アプリケーションに必要なのは下位の `Write` アクセス許可だけです。 可能な場合は、(フォルダーに対して Create アクセス許可を付与するのではなく) 配置時にファイルを作成し、1 つのファイルに対してのみ `Read` アクセス許可を付与する方が安全です。 また、ルート フォルダーや Program Files フォルダーにデータを書き込むよりも、ユーザー フォルダーに書き込む方が安全です。  
  
> [!IMPORTANT]
>  この例では、バイナリ形式のファイルにデータを格納します。 この形式は、パスワードやクレジット カード情報などの重要情報には使用しないでください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="creating-the-loan-object"></a>Loan オブジェクトの作成  
 まず、`Loan` クラスとそのクラスを使用するテスト アプリケーションを作成します。  
  
### <a name="to-create-the-loan-class"></a>Loan クラスを作成するには  
  
1.  新しいクラス ライブラリ プロジェクトを作成して、"LoanClass" という名前を付けます。 詳細については、「[ソリューションとプロジェクトの作成](/visualstudio/ide/creating-solutions-and-projects)」を参照してください。  
  
2.  **ソリューション エクスプローラー**で、Class1 ファイルのショートカット メニューを開き、**[名前の変更]** を選択します。 ファイルの名前を `Loan` に変更し、Enter キーを押します。 ファイルの名前を変更すると、クラスの名前も `Loan` に変更されます。  
  
3.  クラスに次のパブリック メンバーを追加します。  
  
    ```csharp  
    public class Loan : System.ComponentModel.INotifyPropertyChanged  
    {  
        public double LoanAmount {get; set;}  
        public double InterestRate {get; set;}  
        public int Term {get; set;}  
  
        private string p_Customer;  
        public string Customer  
        {  
            get { return p_Customer; }  
            set   
            {  
                p_Customer = value;  
                PropertyChanged(this,  
                  new System.ComponentModel.PropertyChangedEventArgs("Customer"));  
            }  
        }  
  
        public event System.ComponentModel.PropertyChangedEventHandler PropertyChanged;  
  
        public Loan(double loanAmount,  
                    double interestRate,  
                    int term,  
                    string customer)  
        {  
            this.LoanAmount = loanAmount;  
            this.InterestRate = interestRate;  
            this.Term = term;  
            p_Customer = customer;  
        }  
    }  
    ```  
  
 また、`Loan` クラスを使用する簡単なアプリケーションも作成する必要があります。  
  
### <a name="to-create-a-test-application"></a>テスト アプリケーションを作成するには  
  
1.  **[ファイル]** メニューで **[追加]**、**[新しいプロジェクト]** の順に選択し、Windows フォーム アプリケーション プロジェクトをソリューションに追加します。  
  
2.  **[新しいプロジェクトの追加]** ダイアログ ボックスで、**[Windows フォーム アプリケーション]** を選択し、プロジェクト名として「`LoanApp`」と入力します。次に、**[OK]** をクリックしてダイアログ ボックスを閉じます。  
  
3.  **ソリューション エクスプローラー** で LoanApp プロジェクトを選択します。  
  
4.  **[プロジェクト]** メニューの **[スタートアップ プロジェクトに設定]** をクリックします。  
  
5.  **[プロジェクト]** メニューの **[参照の追加]**をクリックします。  
  
6.  **[参照の追加]** ダイアログ ボックスで、**[プロジェクト]** タブをクリックし、LoanClass プロジェクトを選択します。  
  
7.  **[OK]** をクリックしてダイアログ ボックスを閉じます。  
  
8.  デザイナーで、フォームに <xref:System.Windows.Forms.TextBox> コントロールを 4 つ追加します。  
  
9. コード エディターで、次のコードを追加します。  
  
    ```csharp  
    private LoanClass.Loan TestLoan = new LoanClass.Loan(10000.0, 0.075, 36, "Neil Black");  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        textBox1.Text = TestLoan.LoanAmount.ToString();  
        textBox2.Text = TestLoan.InterestRate.ToString();  
        textBox3.Text = TestLoan.Term.ToString();  
        textBox4.Text = TestLoan.Customer;  
    }  
    ```  
  
10. 次のコードを使用して、`PropertyChanged` イベントのイベント ハンドラーをフォームに追加します。  
  
    ```csharp  
    private void CustomerPropertyChanged(object sender,   
        System.ComponentModel.PropertyChangedEventArgs e)  
    {  
        MessageBox.Show(e.PropertyName + " has been changed.");  
    }  
    ```  
  
 この時点で、アプリケーションをビルドして実行できます。 `Loan` クラスの既定値が、テキスト ボックスに表示されます。 利率の値を 7.5 から 7.1 に変更し、アプリケーションをいったん閉じてから、再び実行してください。値が既定値の 7.5 に戻ります。  
  
 実際には利率は定期的に変わりますが、アプリケーションを実行するたびに変わるとは限りません。 アプリケーションを実行するたびにユーザーが利率を更新するのではなく、アプリケーションのインスタンス間で最新の利率を保持できるようにすると便利です。 次の手順では、Loan クラスにシリアル化を追加して、利率を保持できるようにします。  
  
## <a name="using-serialization-to-persist-the-object"></a>シリアル化を使用したオブジェクトの永続化  
 Loan クラスの値を永続化するには、まず、クラスを `Serializable` 属性でマークする必要があります。  
  
### <a name="to-mark-a-class-as-serializable"></a>クラスをシリアル化可能としてマークするには  
  
-   Loan クラスのクラス宣言を次のように変更します。  
  
    ```csharp  
    [Serializable()]  
    public class Loan : System.ComponentModel.INotifyPropertyChanged  
    {  
    ```  
  
 `Serializable` 属性は、クラス内のすべての要素がファイルに永続化できることをコンパイラに示します。 `PropertyChanged` イベントは Windows フォーム オブジェクトで処理されるためシリアル化できません。 永続化しないクラス メンバーは、`NonSerialized` 属性でマークできます。  
  
### <a name="to-prevent-a-member-from-being-serialized"></a>メンバーをシリアル化の対象から除外するには  
  
-   `PropertyChanged` イベントの宣言を次のように変更します。  
  
    ```csharp  
    [field: NonSerialized()]  
    public event System.ComponentModel.PropertyChangedEventHandler PropertyChanged;  
    ```  
  
 次に、LoanApp アプリケーションにシリアル化コードを追加します。 クラスをシリアル化してファイルに書き込むには、<xref:System.IO> 名前空間と <xref:System.Xml.Serialization> 名前空間を使用します。 必要なクラス ライブラリへの参照を追加すると、完全修飾名の入力が不要になります。  
  
### <a name="to-add-references-to-namespaces"></a>名前空間に参照を追加するには  
  
-   `Form1` クラスの先頭に、次のステートメントを追加します。  
  
    ```csharp  
    using System.IO;  
    using System.Runtime.Serialization.Formatters.Binary;  
    ```  
  
     この場合は、バイナリ フォーマッタを使用して、バイナリ形式でオブジェクトを保存します。  
  
 次の手順では、オブジェクトの作成時にファイルからオブジェクトを逆シリアル化するコードを追加します。  
  
### <a name="to-deserialize-an-object"></a>オブジェクトを逆シリアル化するには  
  
1.  シリアル化されたデータのファイル名を定数としてクラスに追加します。  
  
    ```csharp  
    const string FileName = @"..\..\SavedLoan.bin";  
    ```  
  
2.  `Form1_Load` イベント プロシージャのコードを次のように変更します。  
  
    ```csharp  
    private LoanClass.Loan TestLoan = new LoanClass.Loan(10000.0, 0.075, 36, "Neil Black");  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        if (File.Exists(FileName))  
        {  
            Stream TestFileStream = File.OpenRead(FileName);  
            BinaryFormatter deserializer = new BinaryFormatter();  
            TestLoan = (LoanClass.Loan)deserializer.Deserialize(TestFileStream);  
            TestFileStream.Close();  
        }  
  
        TestLoan.PropertyChanged += this.CustomerPropertyChanged;  
  
        textBox1.Text = TestLoan.LoanAmount.ToString();  
        textBox2.Text = TestLoan.InterestRate.ToString();  
        textBox3.Text = TestLoan.Term.ToString();  
        textBox4.Text = TestLoan.Customer;  
    }  
    ```  
  
     まず、ファイルが存在することを確認する必要があります。 ファイルが存在する場合は、バイナリ ファイルを読み取る <xref:System.IO.Stream> クラスと、ファイルを変換する <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> クラスを作成します。 ストリーム型を Loan オブジェクト型に変換する必要もあります。  
  
 次に、テキスト ボックスに入力されたデータを `Loan` クラスに保存するコードを追加します。その後、クラスをファイルにシリアル化する必要があります。  
  
### <a name="to-save-the-data-and-serialize-the-class"></a>データを保存してクラスをシリアル化するには  
  
-   `Form1_FormClosing` イベント プロシージャに次のコードを追加します。  
  
    ```csharp  
    private void Form1_FormClosing(object sender, FormClosingEventArgs e)  
    {  
        TestLoan.LoanAmount = Convert.ToDouble(textBox1.Text);  
        TestLoan.InterestRate = Convert.ToDouble(textBox2.Text);  
        TestLoan.Term = Convert.ToInt32(textBox3.Text);  
        TestLoan.Customer = textBox4.Text;  
  
        Stream TestFileStream = File.Create(FileName);  
        BinaryFormatter serializer = new BinaryFormatter();  
        serializer.Serialize(TestFileStream, TestLoan);  
        TestFileStream.Close();  
    }  
    ```  
  
 この時点で、アプリケーションを再度ビルドして実行できます。 最初に既定値がテキスト ボックスに表示されます。 値を変更して、4 番目のテキスト ボックスに名前を入力します。 いったんアプリケーションを閉じて、再び実行します。 これで、新しい値がテキスト ボックスに表示されます。  
  
## <a name="see-also"></a>参照  
 シリアル化 (C#)[](../../../../csharp/programming-guide/concepts/serialization/index.md)  
 [C# プログラミング ガイド](../../../../csharp/programming-guide/index.md)
