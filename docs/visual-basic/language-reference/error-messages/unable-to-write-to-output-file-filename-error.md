---
title: "出力ファイルに書き込めません &quot;&lt;filename&gt;&quot;:&lt;エラー&gt; |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31019
- bc31019
dev_langs:
- VB
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0822a732390f308b5f8f1f1431299552fb876e74
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="unable-to-write-to-output-file-39ltfilenamegt39-lterrorgt"></a><span data-ttu-id="f3bf1-102">出力ファイルに書き込めません '&lt;filename&gt;':&lt;エラー&gt;</span><span class="sxs-lookup"><span data-stu-id="f3bf1-102">Unable to write to output file &#39;&lt;filename&gt;&#39;: &lt;error&gt;</span></span>
<span data-ttu-id="f3bf1-103">ファイルの作成で問題が発生しました。</span><span class="sxs-lookup"><span data-stu-id="f3bf1-103">There was a problem creating the file.</span></span>  
  
 <span data-ttu-id="f3bf1-104">出力ファイルを書き込み用に開くことができません。</span><span class="sxs-lookup"><span data-stu-id="f3bf1-104">An output file cannot be opened for writing.</span></span> <span data-ttu-id="f3bf1-105">ファイル (または、そのファイルが格納されているフォルダー) は、別のプロセスによって排他的に開かれているか、読み取り専用属性が設定されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f3bf1-105">The file (or the folder containing the file) may be opened for exclusive use by another process, or it may have its read-only attribute set.</span></span>  
  
 <span data-ttu-id="f3bf1-106">ファイルが排他的に開かれている一般的な原因として、次の状況が考えられます。</span><span class="sxs-lookup"><span data-stu-id="f3bf1-106">Common situations where a file is opened exclusively are:</span></span>  
  
-   <span data-ttu-id="f3bf1-107">このアプリケーションが既に実行されていて、ファイルを使用している。</span><span class="sxs-lookup"><span data-stu-id="f3bf1-107">The application is already running and using its files.</span></span> <span data-ttu-id="f3bf1-108">この問題を解決するためには、アプリケーションを終了します。</span><span class="sxs-lookup"><span data-stu-id="f3bf1-108">To solve this problem, make sure that the application is not running.</span></span>  
  
-   <span data-ttu-id="f3bf1-109">別のアプリケーションがファイルを開いている。</span><span class="sxs-lookup"><span data-stu-id="f3bf1-109">Another application has opened the file.</span></span> <span data-ttu-id="f3bf1-110">この問題を解決するためには、ファイルにアクセスしている他のアプリケーションがないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="f3bf1-110">To solve this problem, make sure that no other application is accessing the files.</span></span> <span data-ttu-id="f3bf1-111">ファイルにアクセスしているアプリケーションがわからない場合があります。この場合、アプリケーションを終了する最も簡単な方法として、コンピューターの再起動が考えられます。</span><span class="sxs-lookup"><span data-stu-id="f3bf1-111">It is not always obvious which application is accessing your files; in that case, restarting the computer might be the easiest way to terminate the application.</span></span>  
  
 <span data-ttu-id="f3bf1-112">プロジェクトの出力ファイルのいずれか&1; つだけが読み取り専用になっている場合でも、この例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f3bf1-112">If even one of the project output files is marked as read-only, this exception will be thrown.</span></span>  
  
 <span data-ttu-id="f3bf1-113">**エラー ID:** BC31019</span><span class="sxs-lookup"><span data-stu-id="f3bf1-113">**Error ID:** BC31019</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f3bf1-114">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="f3bf1-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="f3bf1-115">プログラムをもう一度コンパイルし、エラーがまだ発生するかどうか確認します。</span><span class="sxs-lookup"><span data-stu-id="f3bf1-115">Compile the program again to see if the error recurs.</span></span>  
  
2.  <span data-ttu-id="f3bf1-116">エラーが引き続き発生する場合は、作業内容を保存し、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] を再起動します。</span><span class="sxs-lookup"><span data-stu-id="f3bf1-116">If the error continues, save your work and restart [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)].</span></span>  
  
3.  <span data-ttu-id="f3bf1-117">エラーが引き続き発生する場合は、コンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="f3bf1-117">If the error continues, restart the computer.</span></span>  
  
4.  <span data-ttu-id="f3bf1-118">エラーがまだ発生する場合は、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] を再インストールします。</span><span class="sxs-lookup"><span data-stu-id="f3bf1-118">If the error recurs, reinstall [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
5.  <span data-ttu-id="f3bf1-119">再インストールした後にエラーが続く場合は、マイクロソフト プロダクト サポート サービスに通知してください。</span><span class="sxs-lookup"><span data-stu-id="f3bf1-119">If the error persists after reinstallation, notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-check-file-attributes-in-file-explorer"></a><span data-ttu-id="f3bf1-120">エクスプローラーでファイル属性を確認するには</span><span class="sxs-lookup"><span data-stu-id="f3bf1-120">To check file attributes in File Explorer</span></span>  
  
1.  <span data-ttu-id="f3bf1-121">対象のフォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f3bf1-121">Open the folder you are interested in.</span></span>  
  
2.  <span data-ttu-id="f3bf1-122">クリックして、**ビュー**アイコンを選択し、**詳細**します。</span><span class="sxs-lookup"><span data-stu-id="f3bf1-122">Click the **Views** icon and choose **Details**.</span></span>  
  
3.  <span data-ttu-id="f3bf1-123">列ヘッダーを右クリックし **属性**ドロップ ダウン リストからです。</span><span class="sxs-lookup"><span data-stu-id="f3bf1-123">Right-click the column header, and choose **Attributes** from the drop-down list.</span></span>  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a><span data-ttu-id="f3bf1-124">ファイルやフォルダーの属性を変更するには</span><span class="sxs-lookup"><span data-stu-id="f3bf1-124">To change the attributes of a file or folder</span></span>  
  
1.  <span data-ttu-id="f3bf1-125">**ファイル エクスプ ローラー**をファイルまたはフォルダーを右クリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="f3bf1-125">In **File Explorer**, right-click the file or folder and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="f3bf1-126">**属性**のセクションで、**全般**タブで、、**読み取り専用**ボックス。</span><span class="sxs-lookup"><span data-stu-id="f3bf1-126">In the **Attributes** section of the **General** tab, clear the **Read-only** box.</span></span>  
  
3.  <span data-ttu-id="f3bf1-127">Press **OK**.</span><span class="sxs-lookup"><span data-stu-id="f3bf1-127">Press **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3bf1-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3bf1-128">See Also</span></span>  
 [<span data-ttu-id="f3bf1-129">ご意見</span><span class="sxs-lookup"><span data-stu-id="f3bf1-129">Talk to Us</span></span>](https://docs.microsoft.com/visualstudio/ide/talk-to-us)
