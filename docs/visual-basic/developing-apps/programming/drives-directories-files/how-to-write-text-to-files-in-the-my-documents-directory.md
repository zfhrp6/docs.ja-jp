---
title: "方法: My Documents ディレクトリのファイルにテキストを書き込む (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 81eba9a71d90c79f72ccadfa65431754dfb0164e
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="e44f1-102">方法: My Documents ディレクトリのファイルにテキストを書き込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e44f1-102">How to: Write Text to Files in the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="e44f1-103">`My.Computer.FileSystem.SpecialDirectories` オブジェクトを使うと、**[MyDocuments]** ディレクトリなどの特別なディレクトリにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e44f1-103">The `My.Computer.FileSystem.SpecialDirectories` object allows you to access special directories, such as the **MyDocuments** directory.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="e44f1-104">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="e44f1-104">Procedure</span></span>  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a><span data-ttu-id="e44f1-105">[MyDocuments] ディレクトリに新しいテキスト ファイルを書き込むには</span><span class="sxs-lookup"><span data-stu-id="e44f1-105">To write new text files in the My Documents directory</span></span>  
  
1.  <span data-ttu-id="e44f1-106">`My.Computer.FileSystem.SpecialDirectories.MyDocuments` プロパティを使ってパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="e44f1-106">Use the `My.Computer.FileSystem.SpecialDirectories.MyDocuments` property to supply the path.</span></span>  
  
     [!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]  
  
2.  <span data-ttu-id="e44f1-107">`WriteAllText` メソッドを使って、指定したファイルにテキストを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="e44f1-107">Use the `WriteAllText` method to write text to the specified file.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="e44f1-108">例</span><span class="sxs-lookup"><span data-stu-id="e44f1-108">Example</span></span>  
 [!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e44f1-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="e44f1-109">Compiling the Code</span></span>  
 <span data-ttu-id="e44f1-110">`test.txt` を、実際に書き込むファイルの名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="e44f1-110">Replace `test.txt` with the name of the file you want to write to.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e44f1-111">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="e44f1-111">Robust Programming</span></span>  
 <span data-ttu-id="e44f1-112">このコードでは、ファイルにテキストを書き込むときに発生する可能性のあるすべての例外が再スローされます。</span><span class="sxs-lookup"><span data-stu-id="e44f1-112">This code rethrows all the exceptions that may occur when writing text to the file.</span></span> <span data-ttu-id="e44f1-113">ユーザーの選択肢を有効なファイル名に制限する [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) コンポーネントや [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) コンポーネントなどの Windows フォーム コントロールを使うことで、例外が発生する可能性を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="e44f1-113">You can reduce the likelihood of exceptions by using Windows Forms controls such as the [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) and the [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) components that limit the user choices to valid file names.</span></span> <span data-ttu-id="e44f1-114">ただし、これらのコントロールを使ったからといって例外がまったくなくなるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="e44f1-114">Using these controls is not foolproof, however.</span></span> <span data-ttu-id="e44f1-115">ユーザーがファイルを選んだ時点から、コードが実行される時点までの間に、ファイル システムが変化する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e44f1-115">The file system can change between the time the user selects a file and the time that the code executes.</span></span> <span data-ttu-id="e44f1-116">ですから、ファイルを操作するときはほとんど常に、例外処理が必要になります。</span><span class="sxs-lookup"><span data-stu-id="e44f1-116">Exception handling is therefore nearly always necessary when with working with files.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e44f1-117">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e44f1-117">.NET Framework Security</span></span>  
 <span data-ttu-id="e44f1-118">部分的に信頼されたコンテキストで実行している場合、コードは、特権がないために例外をスローする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e44f1-118">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="e44f1-119">詳しくは、「[コード アクセス セキュリティの基礎](../../../../framework/misc/code-access-security-basics.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e44f1-119">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="e44f1-120">この例では、新しいファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="e44f1-120">This example creates a new file.</span></span> <span data-ttu-id="e44f1-121">アプリケーションでファイルを作成する必要がある場合、そのアプリケーションにはフォルダーに対する Create アクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="e44f1-121">If an application needs to create a file, that application needs Create permission for the folder.</span></span> <span data-ttu-id="e44f1-122">アクセス許可は、アクセス制御リストを使って設定します。</span><span class="sxs-lookup"><span data-stu-id="e44f1-122">Permissions are set using access control lists.</span></span> <span data-ttu-id="e44f1-123">ファイルが既に存在する場合、アプリケーションに必要なのは低い権限の Write アクセス許可だけです。</span><span class="sxs-lookup"><span data-stu-id="e44f1-123">If the file already exists, the application needs only Write permission, a lesser privilege.</span></span> <span data-ttu-id="e44f1-124">可能な場合は、フォルダーに対する Create アクセス許可を付与するのではなく、展開の間にファイルを作成しておき、1 つのファイルの Read アクセス許可を付与するだけの方が安全です。</span><span class="sxs-lookup"><span data-stu-id="e44f1-124">Where possible, it is more secure to create the file during deployment, and only grant Read privileges to a single file, rather than to grant Create privileges for a folder.</span></span> <span data-ttu-id="e44f1-125">また、ルート フォルダーや **[Program Files]** フォルダーにデータを書き込むより、ユーザー フォルダーに書き込む方が安全です。</span><span class="sxs-lookup"><span data-stu-id="e44f1-125">Also, it is more secure to write data to user folders than to the root folder or the **Program Files** folder.</span></span> <span data-ttu-id="e44f1-126">詳しくは、「[アクセス制御リスト (ACL: Access Control List) 技術の概要](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e44f1-126">For more information, see [ACL Technology Overview](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e44f1-127">参照</span><span class="sxs-lookup"><span data-stu-id="e44f1-127">See Also</span></span>  
 <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
