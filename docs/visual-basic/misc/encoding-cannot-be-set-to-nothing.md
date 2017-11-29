---
title: "エンコードは Nothing に設定できません"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: daa3567e47f170c64b45cbb9e49d7fa0026b8903
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="encoding-cannot-be-set-to-nothing"></a><span data-ttu-id="01d56-102">エンコードは Nothing に設定できません</span><span class="sxs-lookup"><span data-stu-id="01d56-102">Encoding cannot be set to Nothing</span></span>
<span data-ttu-id="01d56-103">パラメーター `encoding` が `Nothing` に設定されていますが、正しい値が必要なため、ファイルへの読み取りまたは書き込みに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="01d56-103">An attempt to read from or write to a file has failed because the parameter `encoding` has been set to `Nothing` but requires a valid value.</span></span>  
  
 <span data-ttu-id="01d56-104"><xref:System.Text.Encoding> は、ファイルへの書き込み時に使用するエンコードを判別するのに使用されます。</span><span class="sxs-lookup"><span data-stu-id="01d56-104"><xref:System.Text.Encoding> is used to determine what encoding to use when writing to a file.</span></span> <span data-ttu-id="01d56-105">既定は UTF-8 です。</span><span class="sxs-lookup"><span data-stu-id="01d56-105">The default is UTF-8.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="01d56-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="01d56-106">To correct this error</span></span>  
  
-   <span data-ttu-id="01d56-107">正しい値を `encoding` パラメーターに指定します。</span><span class="sxs-lookup"><span data-stu-id="01d56-107">Supply a valid value for the `encoding` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01d56-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="01d56-108">See Also</span></span>  
 [<span data-ttu-id="01d56-109">ファイル エンコーディング</span><span class="sxs-lookup"><span data-stu-id="01d56-109">File Encodings</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 [<span data-ttu-id="01d56-110">ファイルの読み取り</span><span class="sxs-lookup"><span data-stu-id="01d56-110">Reading from Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [<span data-ttu-id="01d56-111">ファイルへの書き込み</span><span class="sxs-lookup"><span data-stu-id="01d56-111">Writing to Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 [<span data-ttu-id="01d56-112">My.Computer.FileSystem.ReadAllText メソッド</span><span class="sxs-lookup"><span data-stu-id="01d56-112">My.Computer.FileSystem.ReadAllText Method</span></span>](http://msdn.microsoft.com/en-us/3a7ac8be-fb1d-4087-bc65-167d6754d57f)  
 [<span data-ttu-id="01d56-113">My.Computer.FileSystem.WriteAllText メソッド</span><span class="sxs-lookup"><span data-stu-id="01d56-113">My.Computer.FileSystem.WriteAllText Method</span></span>](http://msdn.microsoft.com/en-us/f507460c-87d9-4504-b74f-3ff825c7d5c4)
