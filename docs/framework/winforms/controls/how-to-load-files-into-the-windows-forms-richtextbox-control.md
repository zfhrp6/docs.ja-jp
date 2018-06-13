---
title: '方法 : Windows フォームの RichTextBox コントロールにファイルを読み込む'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying files
- examples [Windows Forms], text boxes
- .rtf files [Windows Forms], opening in RichTextBox control
- RTF files [Windows Forms], opening in RichTextBox control
- text files [Windows Forms], displaying in RichTextBox control
- .rtf files [Windows Forms], displaying in RichTextBox control
- RichTextBox control [Windows Forms], opening files
- RTF files [Windows Forms], displaying in RichTextBox control
ms.assetid: c03451be-f285-4428-a71a-c41e002cc919
ms.openlocfilehash: 4d43536cab7806b8cf2de3d63b2d9f7f10024c71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534454"
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a><span data-ttu-id="95c67-102">方法 : Windows フォームの RichTextBox コントロールにファイルを読み込む</span><span class="sxs-lookup"><span data-stu-id="95c67-102">How to: Load Files into the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="95c67-103">Windows フォームの <xref:System.Windows.Forms.RichTextBox> コントロールには、プレーン テキスト、Unicode のプレーン テキスト、リッチ テキスト形式 (RTF) ファイルを表示できます。</span><span class="sxs-lookup"><span data-stu-id="95c67-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display a plain-text, Unicode plain-text, or Rich-Text-Format (RTF) file.</span></span> <span data-ttu-id="95c67-104">それには、 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="95c67-104">To do so, call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method.</span></span> <span data-ttu-id="95c67-105">また、 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> メソッドを使用してストリームからデータを読み込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="95c67-105">You can also use the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method to load data from a stream.</span></span> <span data-ttu-id="95c67-106">詳細については、「 <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95c67-106">For more information, see <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>  
  
### <a name="to-load-a-file-into-the-richtextbox-control"></a><span data-ttu-id="95c67-107">RichTextBox コントロールにファイルを読み込むには</span><span class="sxs-lookup"><span data-stu-id="95c67-107">To load a file into the RichTextBox control</span></span>  
  
1.  <span data-ttu-id="95c67-108"><xref:System.Windows.Forms.OpenFileDialog> コンポーネントを使用して、開くファイルのパスを決定します。</span><span class="sxs-lookup"><span data-stu-id="95c67-108">Determine the path of the file to be opened using the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="95c67-109">概要については、次を参照してください。 [OpenFileDialog コンポーネントの概要](../../../../docs/framework/winforms/controls/openfiledialog-component-overview-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="95c67-109">For an overview, see [OpenFileDialog Component Overview](../../../../docs/framework/winforms/controls/openfiledialog-component-overview-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="95c67-110">読み込むファイルと、必要に応じてファイルの種類を指定して、 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> コントロールの <xref:System.Windows.Forms.RichTextBox> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="95c67-110">Call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to load and optionally a file type.</span></span> <span data-ttu-id="95c67-111">次の例では、読み込むファイルは <xref:System.Windows.Forms.OpenFileDialog> コンポーネントの <xref:System.Windows.Forms.FileDialog.FileName%2A> プロパティから取得されます。</span><span class="sxs-lookup"><span data-stu-id="95c67-111">In the example below, the file to load is taken from the <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.FileDialog.FileName%2A> property.</span></span> <span data-ttu-id="95c67-112">引数にファイル名だけを指定してメソッドを呼び出すと、ファイルの種類は RTF と見なされます。</span><span class="sxs-lookup"><span data-stu-id="95c67-112">If you call the method with a file name as its only argument, the file type will be assumed to be RTF.</span></span> <span data-ttu-id="95c67-113">別の種類のファイルを指定するには、2 番目の引数として <xref:System.Windows.Forms.RichTextBoxStreamType> 列挙型の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="95c67-113">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>  
  
     <span data-ttu-id="95c67-114">次の例では、ボタンがクリックされたときに <xref:System.Windows.Forms.OpenFileDialog> コンポーネントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="95c67-114">In the example below, the <xref:System.Windows.Forms.OpenFileDialog> component is shown when a button is clicked.</span></span> <span data-ttu-id="95c67-115">次に、選択されたファイルが開き、 <xref:System.Windows.Forms.RichTextBox> コントロールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="95c67-115">The file selected is then opened and displayed in the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="95c67-116">この例ではフォームにボタン`btnOpenFile`があることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="95c67-116">This example assumes a form has a button,`btnOpenFile`.</span></span>  
  
    ```vb  
    Private Sub btnOpenFile_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles btnOpenFile.Click  
         If OpenFileDialog1.ShowDialog() = DialogResult.OK Then  
           RichTextBox1.LoadFile(OpenFileDialog1.FileName, _  
              RichTextBoxStreamType.RichText)  
          End If  
    End Sub  
    ```  
  
    ```csharp  
    private void btnOpenFile_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == DialogResult.OK)  
       {  
         richTextBox1.LoadFile(openFileDialog1.FileName, RichTextBoxStreamType.RichText);  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void btnOpenFile_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          if(openFileDialog1->ShowDialog() == DialogResult::OK)  
          {  
             richTextBox1->LoadFile(openFileDialog1->FileName,  
                RichTextBoxStreamType::RichText);  
          }  
       }  
    ```  
  
     <span data-ttu-id="95c67-117">(Visual C# の場合、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="95c67-117">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);  
    ```  
  
    ```cpp  
    this->btnOpenFile->Click += gcnew   
       System::EventHandler(this, &Form1::btnOpenFile_Click);  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="95c67-118">このプロセスを実行するには、アセンブリに対して <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> クラスで特権レベルが許可されていることが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="95c67-118">To run this process, your assembly may require a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="95c67-119">部分的に信頼されたコンテキストで実行している場合、プロセスは、特権がないため例外をスローする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="95c67-119">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="95c67-120">詳しくは、「[コード アクセス セキュリティの基礎](../../../../docs/framework/misc/code-access-security-basics.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="95c67-120">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c67-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="95c67-121">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="95c67-122">RichTextBox コントロール</span><span class="sxs-lookup"><span data-stu-id="95c67-122">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="95c67-123">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="95c67-123">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
