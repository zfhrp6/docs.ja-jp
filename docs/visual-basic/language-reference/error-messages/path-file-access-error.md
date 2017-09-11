---
title: "パス ファイル アクセス エラー |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID75
dev_langs:
- VB
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: 8
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
ms.openlocfilehash: 6307c0d0115e3791d5ad6bf4243057e6ed90d9cd
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="pathfile-access-error"></a><span data-ttu-id="ecac4-102">パス/ファイル アクセス エラー</span><span class="sxs-lookup"><span data-stu-id="ecac4-102">Path/File access error</span></span>
<span data-ttu-id="ecac4-103">ファイル アクセス、またはディスクへのアクセスの操作中に、オペレーティング システムは、パスとファイル名の間の接続を作成できませんでした。</span><span class="sxs-lookup"><span data-stu-id="ecac4-103">During a file-access or disk-access operation, the operating system could not make a connection between the path and the file name.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ecac4-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="ecac4-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="ecac4-105">ファイルの仕様の書式が正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ecac4-105">Make sure the file specification is correctly formatted.</span></span> <span data-ttu-id="ecac4-106">ファイル名は、完全修飾 (絶対値) または相対パスを含めることのパス。</span><span class="sxs-lookup"><span data-stu-id="ecac4-106">A file name can contain a fully qualified (absolute) or relative path.</span></span> <span data-ttu-id="ecac4-107">(パスが別のドライブ上にある場合)、ドライブ名で完全修飾パスを開始し、明示的なルートからファイルへのパスを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="ecac4-107">A fully qualified path starts with the drive name (if the path is on another drive) and lists the explicit path from the root to the file.</span></span> <span data-ttu-id="ecac4-108">完全修飾されていない任意のパスでは、現在のドライブとディレクトリに対して相対的です。</span><span class="sxs-lookup"><span data-stu-id="ecac4-108">Any path that is not fully qualified is relative to the current drive and directory.</span></span>  
  
2.  <span data-ttu-id="ecac4-109">既存の読み取り専用ファイルを置き換えるファイルの保存試みなかったことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ecac4-109">Make sure that you did not attempt to save a file that would replace an existing read-only file.</span></span> <span data-ttu-id="ecac4-110">大文字と小文字の場合は、ターゲット ファイルの読み取り専用属性を変更または別のファイル名、ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="ecac4-110">If this is the case, change the read-only attribute of the target file, or save the file with a different file name.</span></span>  
  
3.  <span data-ttu-id="ecac4-111">シーケンシャルに読み取り専用ファイルを開く試みなかったかどうかを確認`Output`または`Append`モードです。</span><span class="sxs-lookup"><span data-stu-id="ecac4-111">Make sure you did not attempt to open a read-only file in sequential`Output`or `Append` mode.</span></span> <span data-ttu-id="ecac4-112">大文字と小文字の場合でファイルを開きます`Input`モードまたはファイルの読み取り専用属性を変更します。</span><span class="sxs-lookup"><span data-stu-id="ecac4-112">If this is the case, open the file in `Input` mode or change the read-only attribute of the file.</span></span>  
  
4.  <span data-ttu-id="ecac4-113">変更しようとしてしなかったことを確認、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]データベースまたはドキュメント内のプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="ecac4-113">Make sure you did not attempt to change a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] project within a database or document.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecac4-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="ecac4-114">See Also</span></span>  
 [<span data-ttu-id="ecac4-115">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="ecac4-115">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
