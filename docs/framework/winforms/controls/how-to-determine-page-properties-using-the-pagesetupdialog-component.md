---
title: '方法 : PageSetupDialog コンポーネントを使用してページのプロパティを決定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- page properties
- page setup
- PageSetupDialog component
ms.assetid: 6dae05bc-c0fd-4357-bb93-841a1631d98f
ms.openlocfilehash: 4b1acef216e4f8eca078d47a8cde87fb8f95ee0b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532728"
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="db1b0-102">方法 : PageSetupDialog コンポーネントを使用してページのプロパティを決定する</span><span class="sxs-lookup"><span data-stu-id="db1b0-102">How to: Determine Page Properties Using the PageSetupDialog Component</span></span>
<span data-ttu-id="db1b0-103">[PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) コンポーネントは、レイアウト、用紙サイズ、およびその他のページ レイアウトの選択肢をドキュメントのユーザーに示します。</span><span class="sxs-lookup"><span data-stu-id="db1b0-103">The [PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) component presents layout, paper size, and other page layout choices to the user for a document.</span></span>  
  
 <span data-ttu-id="db1b0-104"><xref:System.Drawing.Printing.PrintDocument> クラスのインスタンスを指定する必要があります。これは、印刷するドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="db1b0-104">You need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class—this is the document to be printed.</span></span> <span data-ttu-id="db1b0-105">さらに、ユーザーはコンピューターにローカル プリンターまたはネットワーク プリンターをインストールしておく必要があります。これを基にして、 <xref:System.Windows.Forms.PageSetupDialog> コンポーネントはユーザーに示すページ書式設定選択肢の一部を決定します。</span><span class="sxs-lookup"><span data-stu-id="db1b0-105">Additionally, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PageSetupDialog> component determines the page formatting choices presented to the user.</span></span>  
  
 <span data-ttu-id="db1b0-106"><xref:System.Windows.Forms.PageSetupDialog> コンポーネントを使用するときに重要なことは、 <xref:System.Drawing.Printing.PageSettings> クラスとの対話方法です。</span><span class="sxs-lookup"><span data-stu-id="db1b0-106">An important aspect of working with the <xref:System.Windows.Forms.PageSetupDialog> component is how it interacts with the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="db1b0-107"><xref:System.Drawing.Printing.PageSettings> クラスは、用紙の向き、ページのサイズ、余白など、ページの印刷方法を変更する設定の指定に使用されます。</span><span class="sxs-lookup"><span data-stu-id="db1b0-107">The <xref:System.Drawing.Printing.PageSettings> class is used to specify settings that modify the way a page will be printed, such as paper orientation, the size of the page, and the margins.</span></span> <span data-ttu-id="db1b0-108">これらの各設定は、 <xref:System.Drawing.Printing.PageSettings> クラスのプロパティとして表されます。</span><span class="sxs-lookup"><span data-stu-id="db1b0-108">Each of these settings is represented as a property of the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="db1b0-109"><xref:System.Windows.Forms.PageSetupDialog> クラスは、ドキュメントに関連付けられている (そして、 <xref:System.Drawing.Printing.PageSettings> プロパティとして表されている) <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> クラスの特定のインスタンスに対するこれらのプロパティ値を変更します。</span><span class="sxs-lookup"><span data-stu-id="db1b0-109">The <xref:System.Windows.Forms.PageSetupDialog> class modifies these property values for a given instance of the <xref:System.Drawing.Printing.PageSettings> class that is associated with the document (and is represented as a <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> property).</span></span>  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="db1b0-110">PageSetupDialog コンポーネントを使用してページのプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="db1b0-110">To set page properties using the PageSetupDialog component</span></span>  
  
1.  <span data-ttu-id="db1b0-111"><xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> メソッドを使用してダイアログ ボックスを表示し、使用する <xref:System.Drawing.Printing.PrintDocument> を指定します。</span><span class="sxs-lookup"><span data-stu-id="db1b0-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="db1b0-112">次の例では、 <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Click> イベント ハンドラーが、 <xref:System.Windows.Forms.PageSetupDialog> コンポーネントのインスタンスを開きます。</span><span class="sxs-lookup"><span data-stu-id="db1b0-112">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span> <span data-ttu-id="db1b0-113">既存のドキュメントは <xref:System.Windows.Forms.PageSetupDialog.Document%2A> プロパティで指定され、その <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> プロパティは `false` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="db1b0-113">An existing document is specified in the <xref:System.Windows.Forms.PageSetupDialog.Document%2A> property, and its <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> property is set to `false`.</span></span>  
  
     <span data-ttu-id="db1b0-114">この例では、フォームに、<xref:System.Windows.Forms.Button>コントロール、<xref:System.Drawing.Printing.PrintDocument>という名前のコンポーネント`myDocument`、および<xref:System.Windows.Forms.PageSetupDialog>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="db1b0-114">The example assumes your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       'You will have to specify your own print document.  
       PageSetupDialog1.Document = myDocument  
       ' Sets the print document's color setting to false,  
       ' so that the page will not be printed in color.  
       PageSetupDialog1.Document.DefaultPageSettings.Color = False  
       PageSetupDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       pageSetupDialog1.Document = myDocument;  
       // Sets the print document's color setting to false,  
       // so that the page will not be printed in color.  
       pageSetupDialog1.Document.DefaultPageSettings.Color = false;  
       pageSetupDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void button1_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          pageSetupDialog1->Document = myDocument;  
          // Sets the print document's color setting to false,  
          // so that the page will not be printed in color.  
          pageSetupDialog1->Document->DefaultPageSettings->Color = false;  
          pageSetupDialog1->ShowDialog();  
       }  
    ```  
  
     <span data-ttu-id="db1b0-115">(Visual c# と[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="db1b0-115">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew   
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="db1b0-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="db1b0-116">See Also</span></span>  
 <xref:System.Windows.Forms.PageSetupDialog>  
 [<span data-ttu-id="db1b0-117">方法: 標準の Windows フォーム印刷ジョブを作成する</span><span class="sxs-lookup"><span data-stu-id="db1b0-117">How to: Create Standard Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [<span data-ttu-id="db1b0-118">PageSetupDialog コンポーネント</span><span class="sxs-lookup"><span data-stu-id="db1b0-118">PageSetupDialog Component</span></span>](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)
