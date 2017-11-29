---
title: "単一インスタンスのスタートアップに必要なオペレーティング システムのリソースが取得できないため、予期しないエラーが発生しました。"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8969303d66e946d5579c6cca592b5701c4ebd632
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="810ac-102">単一インスタンスのスタートアップに必要なオペレーティング システムのリソースが取得できないため、予期しないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="810ac-102">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>
<span data-ttu-id="810ac-103">アプリケーションは、必要なオペレーティング システムのリソースを取得できませんでした。</span><span class="sxs-lookup"><span data-stu-id="810ac-103">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="810ac-104">この問題の考えられる原因の一部は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="810ac-104">Some of the possible causes for this problem are:</span></span>  
  
-   <span data-ttu-id="810ac-105">指定されたオペレーティング システム オブジェクトを作成するためのアクセス許可がアプリケーションにない。</span><span class="sxs-lookup"><span data-stu-id="810ac-105">The application does not have permissions to create named operating-system objects.</span></span>  
  
-   <span data-ttu-id="810ac-106">メモリ マップト ファイルを作成するためのアクセス許可が共通言語ランタイムにない。</span><span class="sxs-lookup"><span data-stu-id="810ac-106">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
-   <span data-ttu-id="810ac-107">アプリケーションからオペレーティング システム オブジェクトにアクセスする必要があるが、別のプロセスがそれを使用している。</span><span class="sxs-lookup"><span data-stu-id="810ac-107">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="810ac-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="810ac-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="810ac-109">指定されたオペレーティング システム オブジェクトを作成するための十分なアクセス許可がアプリケーションにあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="810ac-109">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2.  <span data-ttu-id="810ac-110">メモリ マップト ファイルを作成するための十分なアクセス許可が共通言語ランタイムにあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="810ac-110">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3.  <span data-ttu-id="810ac-111">コンピューターを再起動して、元のインスタンス アプリケーションへの接続に必要なリソースを使用している可能性のあるプロセスをすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="810ac-111">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4.  <span data-ttu-id="810ac-112">エラーが発生した状況を記録して、マイクロソフト プロダクト サポート サービスにご連絡ください。</span><span class="sxs-lookup"><span data-stu-id="810ac-112">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="810ac-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="810ac-113">See Also</span></span>  
 <span data-ttu-id="810ac-114">[[アプリケーション] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="810ac-114">[Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)</span></span>  
 [<span data-ttu-id="810ac-115">デバッガーの基本事項</span><span class="sxs-lookup"><span data-stu-id="810ac-115">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)  
 [<span data-ttu-id="810ac-116">ご意見</span><span class="sxs-lookup"><span data-stu-id="810ac-116">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
