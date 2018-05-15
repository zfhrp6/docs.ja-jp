---
title: ファイル モードが正しくありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: bccbbbeb79f38790a4664b0152ca3378fb55448d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="bad-file-mode"></a><span data-ttu-id="6ef00-102">ファイル モードが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="6ef00-102">Bad file mode</span></span>
<span data-ttu-id="6ef00-103">ファイルの内容を操作するときに使用するステートメントは、ファイルが開かれたモードに対応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ef00-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="6ef00-104">以下の原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="6ef00-104">Possible causes include:</span></span>  
  
-   <span data-ttu-id="6ef00-105">A`FilePutObject`または`FileGetObject`ステートメントはシーケンシャル ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="6ef00-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
-   <span data-ttu-id="6ef00-106">A`Print`ステートメント以外の場合、アクセス モードで開かれたファイルを指定する`Output`または`Append`です。</span><span class="sxs-lookup"><span data-stu-id="6ef00-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
-   <span data-ttu-id="6ef00-107">`Input`ステートメント以外の場合、アクセス モードで開かれたファイルを指定します `Input`</span><span class="sxs-lookup"><span data-stu-id="6ef00-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
-   <span data-ttu-id="6ef00-108">読み取り専用ファイルに書き込もうとしています。</span><span class="sxs-lookup"><span data-stu-id="6ef00-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6ef00-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="6ef00-109">To correct this error</span></span>  
  
-   <span data-ttu-id="6ef00-110">確認してください`FilePutObject`と`FileGetObject`の開いているファイルだけが参照され`Random`または`Binary`アクセスします。</span><span class="sxs-lookup"><span data-stu-id="6ef00-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
-   <span data-ttu-id="6ef00-111">確認`Print`のいずれかで開かれるファイルを指定`Output`または`Append`アクセス モードです。</span><span class="sxs-lookup"><span data-stu-id="6ef00-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="6ef00-112">ない場合は、さまざまなステートメントを使用して、データ ファイル内に配置または適切なモードでファイルを閉じて再度開きます。</span><span class="sxs-lookup"><span data-stu-id="6ef00-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
-   <span data-ttu-id="6ef00-113">確認`Input`で開いたファイルを指定`Input`です。</span><span class="sxs-lookup"><span data-stu-id="6ef00-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="6ef00-114">それ以外の場合は、さまざまなステートメントを使用して、データ ファイル内に配置または適切なモードでファイルを閉じて再度開きます。</span><span class="sxs-lookup"><span data-stu-id="6ef00-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
-   <span data-ttu-id="6ef00-115">読み取り専用ファイルに書き込みを行う場合は、ファイルの読み取り/書き込み状態を変更したりへの書き込みをしないでください。</span><span class="sxs-lookup"><span data-stu-id="6ef00-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
-   <span data-ttu-id="6ef00-116">`My.Computer.FileSystem` オブジェクトで利用できる機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="6ef00-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ef00-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ef00-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem>  
 [<span data-ttu-id="6ef00-118">トラブルシューティング : テキスト ファイルの読み取りと書き込み</span><span class="sxs-lookup"><span data-stu-id="6ef00-118">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
