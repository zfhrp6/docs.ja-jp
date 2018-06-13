---
title: '方法 : Windows フォームの RichTextBox コントロールを使用してファイルを保存する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- RTF files [Windows Forms], saving in RichTextBox control
- examples [Windows Forms], text boxes
- saving files [Windows Forms], RichTextBox control
- files [Windows Forms], saving with RichTextBox control
- RichTextBox control [Windows Forms], saving files
- .rtf files [Windows Forms], saving in RichTextBox control
- text files [Windows Forms], saving from RichTextBox control
ms.assetid: 4a58ec19-84d1-4383-9110-298c06adcfca
ms.openlocfilehash: c50b2f3309c1f811b29e824327a709e2cc4bd791
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536196"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="f2c8d-102">方法 : Windows フォームの RichTextBox コントロールを使用してファイルを保存する</span><span class="sxs-lookup"><span data-stu-id="f2c8d-102">How to: Save Files with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="f2c8d-103">Windows フォーム<xref:System.Windows.Forms.RichTextBox>コントロールがいくつかの形式のいずれかで表示される情報を書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="f2c8d-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can write the information it displays in one of several formats:</span></span>  
  
-   <span data-ttu-id="f2c8d-104">プレーンテキスト</span><span class="sxs-lookup"><span data-stu-id="f2c8d-104">Plain text</span></span>  
  
-   <span data-ttu-id="f2c8d-105">Unicode のプレーン テキスト</span><span class="sxs-lookup"><span data-stu-id="f2c8d-105">Unicode plain text</span></span>  
  
-   <span data-ttu-id="f2c8d-106">リッチ テキスト形 (式 RTF)</span><span class="sxs-lookup"><span data-stu-id="f2c8d-106">Rich-Text Format (RTF)</span></span>  
  
-   <span data-ttu-id="f2c8d-107">OLE オブジェクトの代わりにスペースを含む RTF</span><span class="sxs-lookup"><span data-stu-id="f2c8d-107">RTF with spaces in place of OLE objects</span></span>  
  
-   <span data-ttu-id="f2c8d-108">OLE オブジェクトのテキスト表現でプレーン テキスト</span><span class="sxs-lookup"><span data-stu-id="f2c8d-108">Plain text with a textual representation of OLE objects</span></span>  
  
 <span data-ttu-id="f2c8d-109">ファイルを保存するを呼び出して、<xref:System.Windows.Forms.RichTextBox.SaveFile%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f2c8d-109">To save a file, call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method.</span></span> <span data-ttu-id="f2c8d-110">使用することも、 **SaveFile**メソッド データをストリームに保存します。</span><span class="sxs-lookup"><span data-stu-id="f2c8d-110">You can also use the **SaveFile** method to save data to a stream.</span></span> <span data-ttu-id="f2c8d-111">詳細については、「<xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2c8d-111">For more information, see <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a><span data-ttu-id="f2c8d-112">コントロールの内容をファイルに保存するには</span><span class="sxs-lookup"><span data-stu-id="f2c8d-112">To save the contents of the control to a file</span></span>  
  
1.  <span data-ttu-id="f2c8d-113">保存するファイルのパスを決定します。</span><span class="sxs-lookup"><span data-stu-id="f2c8d-113">Determine the path of the file to be saved.</span></span>  
  
     <span data-ttu-id="f2c8d-114">これを行う実際のアプリケーションで、通常使用、<xref:System.Windows.Forms.SaveFileDialog>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="f2c8d-114">To do this in a real-world application, you would typically use the <xref:System.Windows.Forms.SaveFileDialog> component.</span></span> <span data-ttu-id="f2c8d-115">概要については、次を参照してください。 [SaveFileDialog コンポーネントの概要](../../../../docs/framework/winforms/controls/savefiledialog-component-overview-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="f2c8d-115">For an overview, see [SaveFileDialog Component Overview](../../../../docs/framework/winforms/controls/savefiledialog-component-overview-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="f2c8d-116">呼び出す、<xref:System.Windows.Forms.RichTextBox.SaveFile%2A>のメソッド、<xref:System.Windows.Forms.RichTextBox>制御、ファイルを保存して、必要に応じてファイルの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="f2c8d-116">Call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to save and optionally a file type.</span></span> <span data-ttu-id="f2c8d-117">唯一の引数としてファイル名を持つメソッドを呼び出す場合は、rtf 形式で、ファイルが保存されます。</span><span class="sxs-lookup"><span data-stu-id="f2c8d-117">If you call the method with a file name as its only argument, the file will be saved as RTF.</span></span> <span data-ttu-id="f2c8d-118">別の種類のファイルを指定するには、2 番目の引数として <xref:System.Windows.Forms.RichTextBoxStreamType> 列挙型の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="f2c8d-118">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>  
  
     <span data-ttu-id="f2c8d-119">リッチ テキスト ファイルの場所は次の例では、パスを設定、**マイ ドキュメント**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="f2c8d-119">In the example below, the path set for the location of the rich-text file is the **My Documents** folder.</span></span> <span data-ttu-id="f2c8d-120">この場所は、Windows オペレーティング システムを実行しているほとんどのコンピューターがこのフォルダーを含めることを想定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f2c8d-120">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="f2c8d-121">この場所を選択すると、最小限のシステム アクセスのレベルを持つユーザーは、アプリケーションを安全に実行もできます。</span><span class="sxs-lookup"><span data-stu-id="f2c8d-121">Choosing this location also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="f2c8d-122">次の例にフォームを前提としています、<xref:System.Windows.Forms.RichTextBox>コントロールが既に追加されています。</span><span class="sxs-lookup"><span data-stu-id="f2c8d-122">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control already added.</span></span>  
  
    ```vb  
    Public Sub SaveFile()  
       ' You should replace the bold file name in the   
       ' sample below with a file name of your own choosing.  
       RichTextBox1.SaveFile(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Testdoc.rtf", _  
          RichTextBoxStreamType.RichNoOleObjs)  
    End Sub  
    ```  
  
    ```csharp  
    public void SaveFile()  
    {  
       // You should replace the bold file name in the   
       // sample below with a file name of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       richTextBox1.SaveFile(System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Testdoc.rtf",  
          RichTextBoxStreamType.RichNoOleObjs);  
    }  
    ```  
  
    ```cpp  
    public:  
       void SaveFile()  
       {  
          // You should replace the bold file name in the   
          // sample below with a file name of your own choosing.  
          richTextBox1->SaveFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Testdoc.rtf"), RichTextBoxStreamType::RichNoOleObjs);  
       }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="f2c8d-123">次のコード例では、ファイルが存在しない場合は新規にファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="f2c8d-123">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="f2c8d-124">アプリケーション ファイルを作成する場合は、フォルダーの作成アクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="f2c8d-124">If an application needs to create a file, that application needs Create access for the folder.</span></span> <span data-ttu-id="f2c8d-125">アクセス許可は、アクセス制御リストを使って設定します。</span><span class="sxs-lookup"><span data-stu-id="f2c8d-125">Permissions are set using access control lists.</span></span> <span data-ttu-id="f2c8d-126">ファイルが既に存在する場合、アプリケーションには、書き込みアクセスだけより低い権限が必要があります。</span><span class="sxs-lookup"><span data-stu-id="f2c8d-126">If the file already exists, the application needs only Write access, a lesser privilege.</span></span> <span data-ttu-id="f2c8d-127">可能な展開時に、ファイルを作成し、のみ 1 つのファイルに対する読み取りアクセス権を付与ではなくフォルダーのアクセスを作成する方が安全です。</span><span class="sxs-lookup"><span data-stu-id="f2c8d-127">Where possible, it is more secure to create the file during deployment, and only grant Read access to a single file, rather than Create access for a folder.</span></span> <span data-ttu-id="f2c8d-128">また、ルート フォルダーや Program Files フォルダーにデータを書き込むよりも、ユーザー フォルダーに書き込む方が安全です。</span><span class="sxs-lookup"><span data-stu-id="f2c8d-128">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2c8d-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2c8d-129">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="f2c8d-130">RichTextBox コントロール</span><span class="sxs-lookup"><span data-stu-id="f2c8d-130">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="f2c8d-131">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="f2c8d-131">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
