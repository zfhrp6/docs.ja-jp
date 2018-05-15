---
title: Windows フォーム デザイナーでのデザイン時エラー
ms.date: 03/30/2017
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
ms.openlocfilehash: 00296b51563a5f973b8e5d64c55867568ff0324e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a><span data-ttu-id="f5cc4-102">Windows フォーム デザイナーでのデザイン時エラー</span><span class="sxs-lookup"><span data-stu-id="f5cc4-102">Design-Time Errors in the Windows Forms Designer</span></span>
<span data-ttu-id="f5cc4-103">このトピックでは、Windows フォーム デザイナーで読み込みに失敗したときに場合に Microsoft Visual Studio に表示されるデザイン時のエラー リストの意味と使用法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-103">This topic explains the meaning and use of the design-time error list that appears in Microsoft Visual Studio when the Windows Forms Designer fails to load.</span></span> <span data-ttu-id="f5cc4-104">このエラー リストが表示された場合、デザイナーのバグであると解釈するのではなく、コード内のエラーを修正するための参考情報であると考えてください。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-104">If this error list appears, you should not interpret it as a bug in the designer, but as an aid to correcting errors in your code.</span></span>  
  
 <span data-ttu-id="f5cc4-105">エラーに関する詳細情報と考えられる解決策が提示されるので、このエラー リストの基本を理解することによって、アプリケーションのデバッグに役立てることができます。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-105">A basic understanding of this error list will help you debug your applications by providing detailed information about the errors and suggesting possible solutions.</span></span>  
  
## <a name="the-design-time-error-list-interface"></a><span data-ttu-id="f5cc4-106">デザイン時のエラー リスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f5cc4-106">The Design-Time Error List Interface</span></span>  
 <span data-ttu-id="f5cc4-107">Windows フォーム デザイナーで読み込めない場合、デザイナーにエラー リストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-107">If the Windows Forms Designer fails to load, an error list will appear in the designer.</span></span> <span data-ttu-id="f5cc4-108">エラーは複数のカテゴリに分類されています。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-108">The errors are grouped into categories.</span></span> <span data-ttu-id="f5cc4-109">たとえば、宣言されていない変数の 4 つのインスタンスがある場合、それらは同じエラー カテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-109">For example, if you have four instances of undeclared variables, these will be grouped into the same error category.</span></span> <span data-ttu-id="f5cc4-110">各エラー カテゴリには、エラーの概要を示す簡単な説明が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-110">Each error category includes a brief description that summarizes the error.</span></span>  
  
 <span data-ttu-id="f5cc4-111">エラー カテゴリの見出しをクリックするか、展開/折りたたみシェブロンをクリックすることで、エラー カテゴリを展開したり、折りたたんだりできます。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-111">You can expand or collapse an error category by either clicking on the error category heading or by clicking the expand/collapse chevron.</span></span> <span data-ttu-id="f5cc4-112">エラー カテゴリを展開すると、次の追加のヘルプが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-112">When you expand an error category, the following additional help is displayed:</span></span>  
  
-   <span data-ttu-id="f5cc4-113">このエラーのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-113">Instances of this error.</span></span>  
  
-   <span data-ttu-id="f5cc4-114">このエラーのヘルプ。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-114">Help with this error.</span></span>  
  
-   <span data-ttu-id="f5cc4-115">このエラーに関するフォーラムの投稿。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-115">Forum posts about this error.</span></span>  
  
### <a name="instances-of-this-error"></a><span data-ttu-id="f5cc4-116">このエラーのインスタンス</span><span class="sxs-lookup"><span data-stu-id="f5cc4-116">Instances of This Error</span></span>  
 <span data-ttu-id="f5cc4-117">追加のヘルプには、現在のプロジェクトにおけるエラーのすべてのインスタンスが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-117">The additional help list all instances of the error in your current project.</span></span> <span data-ttu-id="f5cc4-118">多くのエラーには、次の形式の正確な場所が含まれます: *[プロジェクト名]* *[フォーム名]* 行:*[行番号]* 列:*[列番号]*。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-118">Many errors include an exact location in the following format: *[Project Name]* *[Form Name]* Line:*[Line Number]* Column:*[Column Number]*.</span></span> <span data-ttu-id="f5cc4-119">**[コードに移動]** リンクを使用して、エラーが発生したコード内の場所に移動できます。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-119">The **Go to code** link takes you to the location in your code where the error occurs.</span></span>  
  
 <span data-ttu-id="f5cc4-120">呼び出し履歴がエラーに関連付けられている場合、**[コール スタックの表示]** リンクをクリックすると、エラーがさらに展開され、呼び出し履歴が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-120">If a call stack is associated with the error, you can click the **Show Call Stack** link, which further expands the error to show the call stack.</span></span> <span data-ttu-id="f5cc4-121">履歴を調べると、有用なデバッグ情報を得られる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-121">Examining the stack can provide valuable debugging information.</span></span> <span data-ttu-id="f5cc4-122">たとえば、エラーが発生する前に呼び出された関数を追跡できます。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-122">For example, you can track the functions that were called before the error occurred.</span></span> <span data-ttu-id="f5cc4-123">呼び出し履歴を選択して、コピーおよび保存できます。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-123">The call stack is selectable so that you can copy and save it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5cc4-124">Visual Basic では、デザイン時エラー リストには複数のエラーは表示されませんが、同じエラーの複数のインスタンスが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-124">In Visual Basic, the design-time error list does not display more than one error, but it may display multiple instances of the same error.</span></span> <span data-ttu-id="f5cc4-125">Visual C++ では、エラーに goto コード リンク/行番号リンクはありません。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-125">In Visual C++, the errors do not have goto code links/line number links.</span></span>  
  
### <a name="help-with-this-error"></a><span data-ttu-id="f5cc4-126">このエラーのヘルプ</span><span class="sxs-lookup"><span data-stu-id="f5cc4-126">Help with This Error</span></span>  
 <span data-ttu-id="f5cc4-127">エラーには、関連する MSDN ヘルプ トピックへのリンクが含まれており、追加のヘルプにはヘルプ トピックへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-127">If the error contains a link to an associated MSDN help topic, the additional help will include a link to the help topic.</span></span> <span data-ttu-id="f5cc4-128">リンクをクリックすると、関連するヘルプ トピックが Visual Studio に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-128">When you click the link, the associated help topic appears in Visual Studio.</span></span>  
  
### <a name="forum-posts-about-this-error"></a><span data-ttu-id="f5cc4-129">このエラーに関するフォーラムの投稿</span><span class="sxs-lookup"><span data-stu-id="f5cc4-129">Forum posts about this error</span></span>  
 <span data-ttu-id="f5cc4-130">追加のヘルプには、エラーに関連する MSDN フォーラムの投稿へのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-130">The additional help will include a link to MSDN forum posts related to the error.</span></span> <span data-ttu-id="f5cc4-131">フォーラムは、エラー メッセージの文字列に基づいて検索されます。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-131">The forums are searched based on the string of the error message.</span></span> <span data-ttu-id="f5cc4-132">次のフォーラムを検索することもできます。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-132">You can also try searching the following forums:</span></span>  
  
-   [<span data-ttu-id="f5cc4-133">Windows フォーム デザイナーのフォーラム</span><span class="sxs-lookup"><span data-stu-id="f5cc4-133">Windows Forms Designer Forum</span></span>](http://go.microsoft.com/fwlink/?LinkId=203524)  
  
-   [<span data-ttu-id="f5cc4-134">Windows フォームのフォーラム</span><span class="sxs-lookup"><span data-stu-id="f5cc4-134">Windows Forms Forums</span></span>](http://go.microsoft.com/fwlink/?LinkId=203523)  
  
### <a name="ignore-and-continue"></a><span data-ttu-id="f5cc4-135">無視して続行する</span><span class="sxs-lookup"><span data-stu-id="f5cc4-135">Ignore and Continue</span></span>  
 <span data-ttu-id="f5cc4-136">エラー状態を無視して、デザイナーの読み込みを続行することもできます。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-136">You can choose to ignore the error condition and continue loading the designer.</span></span> <span data-ttu-id="f5cc4-137">この操作を選択すると、予期しない動作が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-137">Choosing this action may result in unexpected behavior.</span></span> <span data-ttu-id="f5cc4-138">たとえば、デザイン サーフェイスにコントロールが表示されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="f5cc4-138">For example, controls may not appear on the design surface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5cc4-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5cc4-139">See Also</span></span>  
 [<span data-ttu-id="f5cc4-140">デザイン時の開発のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="f5cc4-140">Troubleshooting Design-Time Development</span></span>](http://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [<span data-ttu-id="f5cc4-141">コントロールとコンポーネントの作成時のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="f5cc4-141">Troubleshooting Control and Component Authoring</span></span>](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 [<span data-ttu-id="f5cc4-142">デザイン時の Windows フォーム コントロールの開発</span><span class="sxs-lookup"><span data-stu-id="f5cc4-142">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="f5cc4-143">Windows フォーム デザイナーのエラー メッセージ</span><span class="sxs-lookup"><span data-stu-id="f5cc4-143">Windows Forms Designer Error Messages</span></span>](http://msdn.microsoft.com/library/cf610bf4-5fe4-471c-bce7-6a05ece07bd2)
