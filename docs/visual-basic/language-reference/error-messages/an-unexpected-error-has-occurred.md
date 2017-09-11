---
title: "単一インスタンスの起動に必要なオペレーティング システムのリソースを取得できないため、予期しないエラーが発生しました。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
dev_langs:
- VB
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
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
ms.openlocfilehash: 03ab2d1c746fbc28c0c6f3e59371cc6bbd4050cd
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="68ea1-102">単一インスタンスのスタートアップに必要なオペレーティング システムのリソースが取得できないため、予期しないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="68ea1-102">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>
<span data-ttu-id="68ea1-103">アプリケーションは、必要なオペレーティング システムのリソースを取得できませんでした。</span><span class="sxs-lookup"><span data-stu-id="68ea1-103">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="68ea1-104">この問題の考えられる原因の一部は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="68ea1-104">Some of the possible causes for this problem are:</span></span>  
  
-   <span data-ttu-id="68ea1-105">指定されたオペレーティング システム オブジェクトを作成するためのアクセス許可がアプリケーションにない。</span><span class="sxs-lookup"><span data-stu-id="68ea1-105">The application does not have permissions to create named operating-system objects.</span></span>  
  
-   <span data-ttu-id="68ea1-106">メモリ マップト ファイルを作成するためのアクセス許可が共通言語ランタイムにない。</span><span class="sxs-lookup"><span data-stu-id="68ea1-106">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
-   <span data-ttu-id="68ea1-107">アプリケーションからオペレーティング システム オブジェクトにアクセスする必要があるが、別のプロセスがそれを使用している。</span><span class="sxs-lookup"><span data-stu-id="68ea1-107">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="68ea1-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="68ea1-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="68ea1-109">指定されたオペレーティング システム オブジェクトを作成するための十分なアクセス許可がアプリケーションにあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="68ea1-109">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2.  <span data-ttu-id="68ea1-110">メモリ マップト ファイルを作成するための十分なアクセス許可が共通言語ランタイムにあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="68ea1-110">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3.  <span data-ttu-id="68ea1-111">コンピューターを再起動して、元のインスタンス アプリケーションへの接続に必要なリソースを使用している可能性のあるプロセスをすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="68ea1-111">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4.  <span data-ttu-id="68ea1-112">エラーが発生した状況を記録して、マイクロソフト プロダクト サポート サービスにご連絡ください。</span><span class="sxs-lookup"><span data-stu-id="68ea1-112">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68ea1-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="68ea1-113">See Also</span></span>  
 <span data-ttu-id="68ea1-114">[[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="68ea1-114">[Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic) </span></span>  
<span data-ttu-id="68ea1-115"> [デバッガーの基礎](https://docs.microsoft.com/visualstudio/debugger/debugger-basics) </span><span class="sxs-lookup"><span data-stu-id="68ea1-115"> [Debugger Basics](https://docs.microsoft.com/visualstudio/debugger/debugger-basics) </span></span>  
<span data-ttu-id="68ea1-116"> [ご意見](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span><span class="sxs-lookup"><span data-stu-id="68ea1-116"> [Talk to Us](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span></span>
