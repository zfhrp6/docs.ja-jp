---
title: "この単一インスタンス アプリケーションは、元のインスタンスに接続できませんでした。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 113923e7cb72d1da0a8fb289f29e9afa60dda558
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="bdcaf-102">この単一インスタンス アプリケーションは元のインスタンスに接続できませんでした</span><span class="sxs-lookup"><span data-stu-id="bdcaf-102">This single-instance application could not connect to the original instance</span></span>
<span data-ttu-id="bdcaf-103">この単一インスタンス アプリケーションは元のインスタンスに接続できませんでした。</span><span class="sxs-lookup"><span data-stu-id="bdcaf-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="bdcaf-104">この問題の考えられる原因の一部は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bdcaf-104">Some of the possible causes for this problem are as follows:</span></span>  
  
-   <span data-ttu-id="bdcaf-105">元のインスタンスが応答を停止した。</span><span class="sxs-lookup"><span data-stu-id="bdcaf-105">The original instance stopped responding.</span></span>  
  
-   <span data-ttu-id="bdcaf-106">カーネル オブジェクトを作成するためのアクセス許可がアプリケーションにない。</span><span class="sxs-lookup"><span data-stu-id="bdcaf-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="bdcaf-107">カーネル オブジェクトの詳細については、次を参照してください。[ミュー テックス](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2)します。</span><span class="sxs-lookup"><span data-stu-id="bdcaf-107">For more information about kernel objects, see [Mutexes](http://msdn.microsoft.com/library/9dd06e25-12c0-4a9e-855a-452dc83803e2).</span></span>  
  
     <span data-ttu-id="bdcaf-108">カーネル オブジェクトの基本名は、アセンブリの GUID、メジャー バージョン番号、およびマイナー バージョン番号を連結したものです。</span><span class="sxs-lookup"><span data-stu-id="bdcaf-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="bdcaf-109">たとえば、基本名が `3639f15d-9547-43da-8145-60da347829915.1`になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bdcaf-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="bdcaf-110">アプリケーションを開発しているときに、このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="bdcaf-110">To correct this error when developing the application</span></span>  
  
1.  <span data-ttu-id="bdcaf-111">アプリケーションが応答していない状態にならないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="bdcaf-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2.  <span data-ttu-id="bdcaf-112">カーネル オブジェクトを作成するための十分なアクセス許可がアプリケーションにあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bdcaf-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3.  <span data-ttu-id="bdcaf-113">アプリケーションの元のインスタンスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="bdcaf-113">Restart the original instance of the application.</span></span>  
  
4.  <span data-ttu-id="bdcaf-114">コンピューターを再起動して、元のインスタンス アプリケーションへの接続に必要なリソースを使用している可能性のあるプロセスをすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="bdcaf-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5.  <span data-ttu-id="bdcaf-115">エラーが発生した状況を記録して、Microsoft 製品サポート サービスに電話でご連絡ください。</span><span class="sxs-lookup"><span data-stu-id="bdcaf-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdcaf-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="bdcaf-116">See Also</span></span>  
 <span data-ttu-id="bdcaf-117">[NIB: 方法: アプリケーション (Visual Basic) の動作をインスタンス化を指定します。](http://msdn.microsoft.com/en-us/48539ad8-d960-4210-beab-ee65f6c6dc6e) </span><span class="sxs-lookup"><span data-stu-id="bdcaf-117">[NIB: How to: Specify Instancing Behavior for an Application (Visual Basic)](http://msdn.microsoft.com/en-us/48539ad8-d960-4210-beab-ee65f6c6dc6e) </span></span>  
<span data-ttu-id="bdcaf-118"> [デバッガーの基礎](https://docs.microsoft.com/visualstudio/debugger/debugger-basics) </span><span class="sxs-lookup"><span data-stu-id="bdcaf-118"> [Debugger Basics](https://docs.microsoft.com/visualstudio/debugger/debugger-basics) </span></span>  
<span data-ttu-id="bdcaf-119"> [PAVEOVER 製品のサポートとユーザー補助機能](http://msdn.microsoft.com/en-us/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)</span><span class="sxs-lookup"><span data-stu-id="bdcaf-119"> [PAVEOVER Product Support and Accessibility](http://msdn.microsoft.com/en-us/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)</span></span>
