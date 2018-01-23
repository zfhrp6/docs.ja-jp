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
# <a name="walkthrough-persisting-an-object-in-visual-studio-c"></a><span data-ttu-id="e150a-102">チュートリアル: オブジェクトの永続化 (Visual Studio) (C#)</span><span class="sxs-lookup"><span data-stu-id="e150a-102">Walkthrough: Persisting an Object in Visual Studio (C#)</span></span>
<span data-ttu-id="e150a-103">オブジェクトのプロパティはデザイン時に既定値に設定できますが、そのオブジェクトが破棄されると、実行時に入力した値はすべて失われます。</span><span class="sxs-lookup"><span data-stu-id="e150a-103">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span></span> <span data-ttu-id="e150a-104">シリアル化によってインスタンス間でオブジェクトのデータを永続化すると、値を保存しておき、次にそのオブジェクトをインスタンス化するときに、その値を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="e150a-104">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>  
  
 <span data-ttu-id="e150a-105">このチュートリアルでは、簡単な `Loan` オブジェクトを作成し、そのデータをファイルに永続化します。</span><span class="sxs-lookup"><span data-stu-id="e150a-105">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="e150a-106">その後、オブジェクトを再作成するときに、そのファイルからデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="e150a-106">You will then retrieve the data from the file when you re-create the object.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e150a-107">次の例では、ファイルが存在しない場合は、新しいファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e150a-107">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="e150a-108">アプリケーションでファイルを作成する必要がある場合、そのアプリケーションには、フォルダーに対する `Create` アクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="e150a-108">If an application must create a file, that application must `Create` permission for the folder.</span></span> <span data-ttu-id="e150a-109">アクセス許可は、アクセス制御リストを使用して設定します。</span><span class="sxs-lookup"><span data-stu-id="e150a-109">Permissions are set by using access control lists.</span></span> <span data-ttu-id="e150a-110">ファイルが既に存在する場合、アプリケーションに必要なのは下位の `Write` アクセス許可だけです。</span><span class="sxs-lookup"><span data-stu-id="e150a-110">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="e150a-111">可能な場合は、(フォルダーに対して Create アクセス許可を付与するのではなく) 配置時にファイルを作成し、1 つのファイルに対してのみ `Read` アクセス許可を付与する方が安全です。</span><span class="sxs-lookup"><span data-stu-id="e150a-111">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="e150a-112">また、ルート フォルダーや Program Files フォルダーにデータを書き込むよりも、ユーザー フォルダーに書き込む方が安全です。</span><span class="sxs-lookup"><span data-stu-id="e150a-112">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e150a-113">この例では、バイナリ形式のファイルにデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="e150a-113">This example stores data in a binary format file.</span></span> <span data-ttu-id="e150a-114">この形式は、パスワードやクレジット カード情報などの重要情報には使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="e150a-114">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e150a-115">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e150a-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e150a-116">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e150a-116">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e150a-117">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e150a-117">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-loan-object"></a><span data-ttu-id="e150a-118">Loan オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="e150a-118">Creating the Loan Object</span></span>  
 <span data-ttu-id="e150a-119">まず、`Loan` クラスとそのクラスを使用するテスト アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="e150a-119">The first step is to create a `Loan` class and a test application that uses the class.</span></span>  
  
### <a name="to-create-the-loan-class"></a><span data-ttu-id="e150a-120">Loan クラスを作成するには</span><span class="sxs-lookup"><span data-stu-id="e150a-120">To create the Loan class</span></span>  
  
1.  <span data-ttu-id="e150a-121">新しいクラス ライブラリ プロジェクトを作成して、"LoanClass" という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="e150a-121">Create a new Class Library project and name it "LoanClass".</span></span> <span data-ttu-id="e150a-122">詳細については、「[ソリューションとプロジェクトの作成](/visualstudio/ide/creating-solutions-and-projects)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e150a-122">For more information, see [Creating Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).</span></span>  
  
2.  <span data-ttu-id="e150a-123">**ソリューション エクスプローラー**で、Class1 ファイルのショートカット メニューを開き、**[名前の変更]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e150a-123">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span></span> <span data-ttu-id="e150a-124">ファイルの名前を `Loan` に変更し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="e150a-124">Rename the file to `Loan` and press ENTER.</span></span> <span data-ttu-id="e150a-125">ファイルの名前を変更すると、クラスの名前も `Loan` に変更されます。</span><span class="sxs-lookup"><span data-stu-id="e150a-125">Renaming the file will also rename the class to `Loan`.</span></span>  
  
3.  <span data-ttu-id="e150a-126">クラスに次のパブリック メンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="e150a-126">Add the following public members to the class:</span></span>  
  
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
  
 <span data-ttu-id="e150a-127">また、`Loan` クラスを使用する簡単なアプリケーションも作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e150a-127">You will also have to create a simple application that uses the `Loan` class.</span></span>  
  
### <a name="to-create-a-test-application"></a><span data-ttu-id="e150a-128">テスト アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="e150a-128">To create a test application</span></span>  
  
1.  <span data-ttu-id="e150a-129">**[ファイル]** メニューで **[追加]**、**[新しいプロジェクト]** の順に選択し、Windows フォーム アプリケーション プロジェクトをソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="e150a-129">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="e150a-130">**[新しいプロジェクトの追加]** ダイアログ ボックスで、**[Windows フォーム アプリケーション]** を選択し、プロジェクト名として「`LoanApp`」と入力します。次に、**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e150a-130">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span></span>  
  
3.  <span data-ttu-id="e150a-131">**ソリューション エクスプローラー** で LoanApp プロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="e150a-131">In **Solution Explorer**, choose the LoanApp project.</span></span>  
  
4.  <span data-ttu-id="e150a-132">**[プロジェクト]** メニューの **[スタートアップ プロジェクトに設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e150a-132">On the **Project** menu, choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="e150a-133">**[プロジェクト]** メニューの **[参照の追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e150a-133">On the **Project** menu, choose **Add Reference**.</span></span>  
  
6.  <span data-ttu-id="e150a-134">**[参照の追加]** ダイアログ ボックスで、**[プロジェクト]** タブをクリックし、LoanClass プロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="e150a-134">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span></span>  
  
7.  <span data-ttu-id="e150a-135">**[OK]** をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e150a-135">Click **OK** to close the dialog box.</span></span>  
  
8.  <span data-ttu-id="e150a-136">デザイナーで、フォームに <xref:System.Windows.Forms.TextBox> コントロールを 4 つ追加します。</span><span class="sxs-lookup"><span data-stu-id="e150a-136">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span></span>  
  
9. <span data-ttu-id="e150a-137">コード エディターで、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e150a-137">In the Code Editor, add the following code:</span></span>  
  
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
  
10. <span data-ttu-id="e150a-138">次のコードを使用して、`PropertyChanged` イベントのイベント ハンドラーをフォームに追加します。</span><span class="sxs-lookup"><span data-stu-id="e150a-138">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span></span>  
  
    ```csharp  
    private void CustomerPropertyChanged(object sender,   
        System.ComponentModel.PropertyChangedEventArgs e)  
    {  
        MessageBox.Show(e.PropertyName + " has been changed.");  
    }  
    ```  
  
 <span data-ttu-id="e150a-139">この時点で、アプリケーションをビルドして実行できます。</span><span class="sxs-lookup"><span data-stu-id="e150a-139">At this point, you can build and run the application.</span></span> <span data-ttu-id="e150a-140">`Loan` クラスの既定値が、テキスト ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e150a-140">Note that the default values from the `Loan` class appear in the text boxes.</span></span> <span data-ttu-id="e150a-141">利率の値を 7.5 から 7.1 に変更し、アプリケーションをいったん閉じてから、再び実行してください。値が既定値の 7.5 に戻ります。</span><span class="sxs-lookup"><span data-stu-id="e150a-141">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span></span>  
  
 <span data-ttu-id="e150a-142">実際には利率は定期的に変わりますが、アプリケーションを実行するたびに変わるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="e150a-142">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="e150a-143">アプリケーションを実行するたびにユーザーが利率を更新するのではなく、アプリケーションのインスタンス間で最新の利率を保持できるようにすると便利です。</span><span class="sxs-lookup"><span data-stu-id="e150a-143">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="e150a-144">次の手順では、Loan クラスにシリアル化を追加して、利率を保持できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e150a-144">In the next step, you will do just that by adding serialization to the Loan class.</span></span>  
  
## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="e150a-145">シリアル化を使用したオブジェクトの永続化</span><span class="sxs-lookup"><span data-stu-id="e150a-145">Using Serialization to Persist the Object</span></span>  
 <span data-ttu-id="e150a-146">Loan クラスの値を永続化するには、まず、クラスを `Serializable` 属性でマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e150a-146">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span>  
  
### <a name="to-mark-a-class-as-serializable"></a><span data-ttu-id="e150a-147">クラスをシリアル化可能としてマークするには</span><span class="sxs-lookup"><span data-stu-id="e150a-147">To mark a class as serializable</span></span>  
  
-   <span data-ttu-id="e150a-148">Loan クラスのクラス宣言を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="e150a-148">Change the class declaration for the Loan class as follows:</span></span>  
  
    ```csharp  
    [Serializable()]  
    public class Loan : System.ComponentModel.INotifyPropertyChanged  
    {  
    ```  
  
 <span data-ttu-id="e150a-149">`Serializable` 属性は、クラス内のすべての要素がファイルに永続化できることをコンパイラに示します。</span><span class="sxs-lookup"><span data-stu-id="e150a-149">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="e150a-150">`PropertyChanged` イベントは Windows フォーム オブジェクトで処理されるためシリアル化できません。</span><span class="sxs-lookup"><span data-stu-id="e150a-150">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span></span> <span data-ttu-id="e150a-151">永続化しないクラス メンバーは、`NonSerialized` 属性でマークできます。</span><span class="sxs-lookup"><span data-stu-id="e150a-151">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span></span>  
  
### <a name="to-prevent-a-member-from-being-serialized"></a><span data-ttu-id="e150a-152">メンバーをシリアル化の対象から除外するには</span><span class="sxs-lookup"><span data-stu-id="e150a-152">To prevent a member from being serialized</span></span>  
  
-   <span data-ttu-id="e150a-153">`PropertyChanged` イベントの宣言を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="e150a-153">Change the declaration for the `PropertyChanged` event as follows:</span></span>  
  
    ```csharp  
    [field: NonSerialized()]  
    public event System.ComponentModel.PropertyChangedEventHandler PropertyChanged;  
    ```  
  
 <span data-ttu-id="e150a-154">次に、LoanApp アプリケーションにシリアル化コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e150a-154">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="e150a-155">クラスをシリアル化してファイルに書き込むには、<xref:System.IO> 名前空間と <xref:System.Xml.Serialization> 名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="e150a-155">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span></span> <span data-ttu-id="e150a-156">必要なクラス ライブラリへの参照を追加すると、完全修飾名の入力が不要になります。</span><span class="sxs-lookup"><span data-stu-id="e150a-156">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span></span>  
  
### <a name="to-add-references-to-namespaces"></a><span data-ttu-id="e150a-157">名前空間に参照を追加するには</span><span class="sxs-lookup"><span data-stu-id="e150a-157">To add references to namespaces</span></span>  
  
-   <span data-ttu-id="e150a-158">`Form1` クラスの先頭に、次のステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="e150a-158">Add the following statements to the top of the `Form1` class:</span></span>  
  
    ```csharp  
    using System.IO;  
    using System.Runtime.Serialization.Formatters.Binary;  
    ```  
  
     <span data-ttu-id="e150a-159">この場合は、バイナリ フォーマッタを使用して、バイナリ形式でオブジェクトを保存します。</span><span class="sxs-lookup"><span data-stu-id="e150a-159">In this case, you are using a binary formatter to save the object in a binary format.</span></span>  
  
 <span data-ttu-id="e150a-160">次の手順では、オブジェクトの作成時にファイルからオブジェクトを逆シリアル化するコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e150a-160">The next step is to add code to deserialize the object from the file when the object is created.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="e150a-161">オブジェクトを逆シリアル化するには</span><span class="sxs-lookup"><span data-stu-id="e150a-161">To deserialize an object</span></span>  
  
1.  <span data-ttu-id="e150a-162">シリアル化されたデータのファイル名を定数としてクラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="e150a-162">Add a constant to the class for the serialized data's file name.</span></span>  
  
    ```csharp  
    const string FileName = @"..\..\SavedLoan.bin";  
    ```  
  
2.  <span data-ttu-id="e150a-163">`Form1_Load` イベント プロシージャのコードを次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="e150a-163">Modify the code in the `Form1_Load` event procedure as follows:</span></span>  
  
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
  
     <span data-ttu-id="e150a-164">まず、ファイルが存在することを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e150a-164">Note that you first must check that the file exists.</span></span> <span data-ttu-id="e150a-165">ファイルが存在する場合は、バイナリ ファイルを読み取る <xref:System.IO.Stream> クラスと、ファイルを変換する <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e150a-165">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="e150a-166">ストリーム型を Loan オブジェクト型に変換する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="e150a-166">You also need to convert from the stream type to the Loan object type.</span></span>  
  
 <span data-ttu-id="e150a-167">次に、テキスト ボックスに入力されたデータを `Loan` クラスに保存するコードを追加します。その後、クラスをファイルにシリアル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e150a-167">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span></span>  
  
### <a name="to-save-the-data-and-serialize-the-class"></a><span data-ttu-id="e150a-168">データを保存してクラスをシリアル化するには</span><span class="sxs-lookup"><span data-stu-id="e150a-168">To save the data and serialize the class</span></span>  
  
-   <span data-ttu-id="e150a-169">`Form1_FormClosing` イベント プロシージャに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e150a-169">Add the following code to the `Form1_FormClosing` event procedure:</span></span>  
  
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
  
 <span data-ttu-id="e150a-170">この時点で、アプリケーションを再度ビルドして実行できます。</span><span class="sxs-lookup"><span data-stu-id="e150a-170">At this point, you can again build and run the application.</span></span> <span data-ttu-id="e150a-171">最初に既定値がテキスト ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e150a-171">Initially, the default values appear in the text boxes.</span></span> <span data-ttu-id="e150a-172">値を変更して、4 番目のテキスト ボックスに名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="e150a-172">Try to change the values and enter a name in the fourth text box.</span></span> <span data-ttu-id="e150a-173">いったんアプリケーションを閉じて、再び実行します。</span><span class="sxs-lookup"><span data-stu-id="e150a-173">Close the application and then run it again.</span></span> <span data-ttu-id="e150a-174">これで、新しい値がテキスト ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e150a-174">Note that the new values now appear in the text boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e150a-175">参照</span><span class="sxs-lookup"><span data-stu-id="e150a-175">See Also</span></span>  
 <span data-ttu-id="e150a-176">シリアル化 (C#)[](../../../../csharp/programming-guide/concepts/serialization/index.md)</span><span class="sxs-lookup"><span data-stu-id="e150a-176">[Serialization (C# )](../../../../csharp/programming-guide/concepts/serialization/index.md)</span></span>  
 [<span data-ttu-id="e150a-177">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="e150a-177">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
