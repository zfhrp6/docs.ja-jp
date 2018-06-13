---
title: '方法 : OpenFileDialog コンポーネントを使用してファイルを開く'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: d7e1ebb319576aa7a38d55d8cb9f3652626966b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542276"
---
# <a name="how-to-open-files-using-the-openfiledialog-component"></a><span data-ttu-id="986b1-102">方法 : OpenFileDialog コンポーネントを使用してファイルを開く</span><span class="sxs-lookup"><span data-stu-id="986b1-102">How to: Open Files Using the OpenFileDialog Component</span></span>
<span data-ttu-id="986b1-103"><xref:System.Windows.Forms.OpenFileDialog>コンポーネントにより、ユーザーが自分のコンピューターまたはネットワーク上のコンピューターのフォルダーを参照し、1 つまたは複数のファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="986b1-103">The <xref:System.Windows.Forms.OpenFileDialog> component allows users to browse the folders of their computer or any computer on the network and select one or more files to open.</span></span> <span data-ttu-id="986b1-104">このダイアログ ボックスは、ユーザーがダイアログ ボックス内で選択したファイルのパスと名前を返します。</span><span class="sxs-lookup"><span data-stu-id="986b1-104">The dialog box returns the path and name of the file the user selected in the dialog box.</span></span>  
  
 <span data-ttu-id="986b1-105">ユーザーが開くファイルを選択したら、そのファイルを開く方法として 2 とおりのアプローチがあります。</span><span class="sxs-lookup"><span data-stu-id="986b1-105">Once the user has selected the file to be opened, there are two approaches to the mechanism of opening the file.</span></span> <span data-ttu-id="986b1-106">ファイル ストリームを使用する場合は、インスタンスを作成することができます、<xref:System.IO.StreamReader>クラスです。</span><span class="sxs-lookup"><span data-stu-id="986b1-106">If you prefer to work with file streams, you can create an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="986b1-107">また、使用することができます、<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>を選択したファイルを開くメソッドです。</span><span class="sxs-lookup"><span data-stu-id="986b1-107">Alternately, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open the selected file.</span></span>  
  
 <span data-ttu-id="986b1-108">次の最初の例では、<xref:System.Security.Permissions.FileIOPermission>が、アクセス許可のチェック (下の「セキュリティに関する注意」で説明) と、ファイル名にアクセスすることです。</span><span class="sxs-lookup"><span data-stu-id="986b1-108">The first example below involves a <xref:System.Security.Permissions.FileIOPermission> permission check (as described in the "Security Note" below), but gives you access to the filename.</span></span> <span data-ttu-id="986b1-109">この手法は、ローカル コンピューター、イントラネット、およびインターネットの各ゾーンから利用できます。</span><span class="sxs-lookup"><span data-stu-id="986b1-109">You can use this technique from the Local Machine, Intranet, and Internet zones.</span></span> <span data-ttu-id="986b1-110">また、2 番目のメソッドも実行、<xref:System.Security.Permissions.FileIOPermission>権限チェックがより、イントラネットまたはインターネット ゾーンでのアプリケーションに適しています。</span><span class="sxs-lookup"><span data-stu-id="986b1-110">The second method also does a <xref:System.Security.Permissions.FileIOPermission> permission check, but is better suited for applications in the Intranet or Internet zones.</span></span>  
  
### <a name="to-open-a-file-as-a-stream-using-the-openfiledialog-component"></a><span data-ttu-id="986b1-111">OpenFileDialog コンポーネントを使用してファイルをストリームとして開くには</span><span class="sxs-lookup"><span data-stu-id="986b1-111">To open a file as a stream using the OpenFileDialog component</span></span>  
  
1.  <span data-ttu-id="986b1-112">**[ファイルを開く]** ダイアログ ボックスを表示し、ユーザーによって選択されたファイルを開くメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="986b1-112">Display the **Open File** dialog box and call a method to open the file selected by the user.</span></span>  
  
     <span data-ttu-id="986b1-113">1 つの方法は、使用する、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッドのインスタンスを使用してファイルを開く ダイアログ ボックスを表示、<xref:System.IO.StreamReader>クラス ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="986b1-113">One approach is to use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the Open File dialog box, and use an instance of the <xref:System.IO.StreamReader> class to open the file.</span></span>  
  
     <span data-ttu-id="986b1-114">使用して次の例、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Click>イベント ハンドラーのインスタンスを開く、<xref:System.Windows.Forms.OpenFileDialog>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="986b1-114">The example below uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open an instance of the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="986b1-115">ファイルが選択され、ユーザーが **[OK]** をクリックすると、ダイアログ ボックスで選択されたファイルが開きます。</span><span class="sxs-lookup"><span data-stu-id="986b1-115">When a file is chosen and the user clicks **OK**, the file selected in the dialog box opens.</span></span> <span data-ttu-id="986b1-116">この場合、ファイルの内容はメッセージ ボックスに表示され、ファイル ストリームが読み取られたことが単に示されます。</span><span class="sxs-lookup"><span data-stu-id="986b1-116">In this case, the contents are displayed in a message box, just to show that the file stream has been read.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="986b1-117">取得または設定する、<xref:System.Windows.Forms.FileDialog.FileName%2A>プロパティをアセンブリが必要です、特権レベル許可によって、<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>クラスです。</span><span class="sxs-lookup"><span data-stu-id="986b1-117">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="986b1-118">部分的に信頼されたコンテキストで実行している場合、プロセスは、特権がないために例外をスローする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="986b1-118">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="986b1-119">詳しくは、「[コード アクセス セキュリティの基礎](../../../../docs/framework/misc/code-access-security-basics.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="986b1-119">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="986b1-120">この例では、フォームには、<xref:System.Windows.Forms.Button>コントロールと<xref:System.Windows.Forms.OpenFileDialog>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="986b1-120">The example assumes your form has a <xref:System.Windows.Forms.Button> control and an <xref:System.Windows.Forms.OpenFileDialog> component.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If OpenFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         Dim sr As New System.IO.StreamReader(OpenFileDialog1.FileName)  
         MessageBox.Show(sr.ReadToEnd)  
         sr.Close()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          System.IO.StreamReader sr = new   
             System.IO.StreamReader(openFileDialog1.FileName);  
          MessageBox.Show(sr.ReadToEnd());  
          sr.Close();  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             System::IO::StreamReader ^ sr = gcnew  
                System::IO::StreamReader(openFileDialog1->FileName);  
             MessageBox::Show(sr->ReadToEnd());  
             sr->Close();  
          }  
       }  
    ```  
  
     <span data-ttu-id="986b1-121">(Visual c# と[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="986b1-121">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="986b1-122">ファイル ストリームからの読み取りの詳細については、次を参照してください。<xref:System.IO.FileStream.BeginRead%2A>と<xref:System.IO.FileStream.Read%2A>です。</span><span class="sxs-lookup"><span data-stu-id="986b1-122">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A> and <xref:System.IO.FileStream.Read%2A>.</span></span>  
  
### <a name="to-open-a-file-as-a-file-using-the-openfiledialog-component"></a><span data-ttu-id="986b1-123">OpenFileDialog コンポーネントを使用してファイルをファイルとして開くには</span><span class="sxs-lookup"><span data-stu-id="986b1-123">To open a file as a file using the OpenFileDialog component</span></span>  
  
1.  <span data-ttu-id="986b1-124">使用して、 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>  ダイアログ ボックスを表示する方法、および<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>ファイルを開くメソッドです。</span><span class="sxs-lookup"><span data-stu-id="986b1-124">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open the file.</span></span>  
  
     <span data-ttu-id="986b1-125"><xref:System.Windows.Forms.OpenFileDialog>コンポーネントの<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>メソッドは、ファイルを構成するバイトを返します。</span><span class="sxs-lookup"><span data-stu-id="986b1-125">The <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method returns the bytes that compose the file.</span></span> <span data-ttu-id="986b1-126">これらのバイトにより、読み取り元のストリームが提供されます。</span><span class="sxs-lookup"><span data-stu-id="986b1-126">These bytes give you a stream to read from.</span></span> <span data-ttu-id="986b1-127">次の例で、<xref:System.Windows.Forms.OpenFileDialog>コンポーネントが"cursor"にフィルターを適用し、ユーザーがファイル名拡張子を持つファイルだけを選択できるようにインスタンス化される`.cur`です。</span><span class="sxs-lookup"><span data-stu-id="986b1-127">In the example below, an <xref:System.Windows.Forms.OpenFileDialog> component is instantiated with a "cursor" filter on it, allowing the user to choose only files with the file name extension`.cur`.</span></span> <span data-ttu-id="986b1-128">`.cur` ファイルが選択されると、フォームのカーソルが選択されたカーソルに設定されます。</span><span class="sxs-lookup"><span data-stu-id="986b1-128">If a`.cur` file is chosen, the form's cursor is set to the selected cursor.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="986b1-129">呼び出す、<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>メソッド、アセンブリが必要です、特権レベル許可によって、<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>クラスです。</span><span class="sxs-lookup"><span data-stu-id="986b1-129">To call the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="986b1-130">部分的に信頼されたコンテキストで実行している場合、プロセスは、特権がないために例外をスローする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="986b1-130">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="986b1-131">詳しくは、「[コード アクセス セキュリティの基礎](../../../../docs/framework/misc/code-access-security-basics.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="986b1-131">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="986b1-132">この例では、フォームには、<xref:System.Windows.Forms.Button>コントロール。</span><span class="sxs-lookup"><span data-stu-id="986b1-132">The example assumes your form has a <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' Displays an OpenFileDialog so the user can select a Cursor.  
       Dim openFileDialog1 As New OpenFileDialog()  
       openFileDialog1.Filter = "Cursor Files|*.cur"  
       openFileDialog1.Title = "Select a Cursor File"  
  
       ' Show the Dialog.  
       ' If the user clicked OK in the dialog and   
       ' a .CUR file was selected, open it.  
       If openFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         ' Assign the cursor in the Stream to the Form's Cursor property.  
         Me.Cursor = New Cursor(openFileDialog1.OpenFile())  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // Displays an OpenFileDialog so the user can select a Cursor.  
       OpenFileDialog openFileDialog1 = new OpenFileDialog();  
       openFileDialog1.Filter = "Cursor Files|*.cur";  
       openFileDialog1.Title = "Select a Cursor File";  
  
       // Show the Dialog.  
       // If the user clicked OK in the dialog and  
       // a .CUR file was selected, open it.  
        if (openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          // Assign the cursor in the Stream to the Form's Cursor property.  
          this.Cursor = new Cursor(openFileDialog1.OpenFile());  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays an OpenFileDialog so the user can select a Cursor.  
          OpenFileDialog ^ openFileDialog1 = new OpenFileDialog();  
          openFileDialog1->Filter = "Cursor Files|*.cur";  
          openFileDialog1->Title = "Select a Cursor File";  
  
          // Show the Dialog.  
          // If the user clicked OK in the dialog and  
          // a .CUR file was selected, open it.  
          if (openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             // Assign the cursor in the Stream to  
             // the Form's Cursor property.  
             this->Cursor = gcnew  
                System::Windows::Forms::Cursor(  
                openFileDialog1->OpenFile());  
          }  
       }  
    ```  
  
     <span data-ttu-id="986b1-133">(Visual c# と[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="986b1-133">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="986b1-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="986b1-134">See Also</span></span>  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [<span data-ttu-id="986b1-135">OpenFileDialog コンポーネント</span><span class="sxs-lookup"><span data-stu-id="986b1-135">OpenFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
