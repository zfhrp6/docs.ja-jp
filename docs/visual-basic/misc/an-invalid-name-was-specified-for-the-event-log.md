---
title: "イベント ログに無効な名前が指定されました"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76e4082710a6786ec5e743ce606e849637c26512
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="748bc-102">イベント ログに無効な名前が指定されました</span><span class="sxs-lookup"><span data-stu-id="748bc-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="748bc-103">イベント ログに無効な名前が指定されました。</span><span class="sxs-lookup"><span data-stu-id="748bc-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="748bc-104">通常これは、名前に含まれる無効な文字、空のファイル名、または長すぎるファイル名の結果です。</span><span class="sxs-lookup"><span data-stu-id="748bc-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="748bc-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="748bc-105">To correct this error</span></span>  
  
-   <span data-ttu-id="748bc-106">指定した名前が 8 文字を超える場合、他のイベント ログの名前と競合しないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="748bc-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="748bc-107">名前が一意であるかどうかを判断するときには、最初の 8 文字のみが評価されます。</span><span class="sxs-lookup"><span data-stu-id="748bc-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
-   <span data-ttu-id="748bc-108">パスを指定する場合は、正しく解析されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="748bc-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
-   <span data-ttu-id="748bc-109">名前に無効な文字がないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="748bc-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="748bc-110">ファイル名に使用できない文字には `<`、 `>`、 `:`、 `"`、 `/`、 `\`、および `|`があります。</span><span class="sxs-lookup"><span data-stu-id="748bc-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="748bc-111">参照</span><span class="sxs-lookup"><span data-stu-id="748bc-111">See Also</span></span>  
 [<span data-ttu-id="748bc-112">方法: ファイル パスを解析する</span><span class="sxs-lookup"><span data-stu-id="748bc-112">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)  
 [<span data-ttu-id="748bc-113">方法: ファイルの名前を変更する</span><span class="sxs-lookup"><span data-stu-id="748bc-113">How to: Rename a File</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 
