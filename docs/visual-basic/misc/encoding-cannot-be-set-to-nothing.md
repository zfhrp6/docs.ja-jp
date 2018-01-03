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
ms.openlocfilehash: 42baef6e0634849004290dce3db32e47f103282d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="encoding-cannot-be-set-to-nothing"></a><span data-ttu-id="7a677-102">エンコードは Nothing に設定できません</span><span class="sxs-lookup"><span data-stu-id="7a677-102">Encoding cannot be set to Nothing</span></span>
<span data-ttu-id="7a677-103">パラメーター `encoding` が `Nothing` に設定されていますが、正しい値が必要なため、ファイルへの読み取りまたは書き込みに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="7a677-103">An attempt to read from or write to a file has failed because the parameter `encoding` has been set to `Nothing` but requires a valid value.</span></span>  
  
 <span data-ttu-id="7a677-104"><xref:System.Text.Encoding> は、ファイルへの書き込み時に使用するエンコードを判別するのに使用されます。</span><span class="sxs-lookup"><span data-stu-id="7a677-104"><xref:System.Text.Encoding> is used to determine what encoding to use when writing to a file.</span></span> <span data-ttu-id="7a677-105">既定は UTF-8 です。</span><span class="sxs-lookup"><span data-stu-id="7a677-105">The default is UTF-8.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7a677-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="7a677-106">To correct this error</span></span>  
  
-   <span data-ttu-id="7a677-107">正しい値を `encoding` パラメーターに指定します。</span><span class="sxs-lookup"><span data-stu-id="7a677-107">Supply a valid value for the `encoding` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a677-108">参照</span><span class="sxs-lookup"><span data-stu-id="7a677-108">See Also</span></span>  
 [<span data-ttu-id="7a677-109">ファイル エンコーディング</span><span class="sxs-lookup"><span data-stu-id="7a677-109">File Encodings</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 [<span data-ttu-id="7a677-110">ファイルの読み取り</span><span class="sxs-lookup"><span data-stu-id="7a677-110">Reading from Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [<span data-ttu-id="7a677-111">ファイルへの書き込み</span><span class="sxs-lookup"><span data-stu-id="7a677-111">Writing to Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 [<span data-ttu-id="7a677-112">My.Computer.FileSystem.ReadAllText</span><span class="sxs-lookup"><span data-stu-id="7a677-112">My.Computer.FileSystem.ReadAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)  
 [<span data-ttu-id="7a677-113">My.Computer.FileSystem.WriteAllText</span><span class="sxs-lookup"><span data-stu-id="7a677-113">My.Computer.FileSystem.WriteAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
