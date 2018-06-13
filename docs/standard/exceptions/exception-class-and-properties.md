---
title: Exception クラスとプロパティ
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9cdc464234871fc07feeeb8dd02635ebdd151d76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573198"
---
# <a name="exception-class-and-properties"></a><span data-ttu-id="fc5db-102">Exception クラスとプロパティ</span><span class="sxs-lookup"><span data-stu-id="fc5db-102">Exception class and properties</span></span>

<span data-ttu-id="fc5db-103"><xref:System.Exception> クラスは、例外の継承元となる基底クラスです。</span><span class="sxs-lookup"><span data-stu-id="fc5db-103">The <xref:System.Exception> class is the base class from which exceptions inherit.</span></span> <span data-ttu-id="fc5db-104">たとえば、<xref:System.InvalidCastException> クラスの階層は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="fc5db-104">For example, the <xref:System.InvalidCastException> class hierarchy is as follows:</span></span>

```
Object
  Exception
    SystemException
       InvalidCastException
```

<span data-ttu-id="fc5db-105"><xref:System.Exception> クラスには、簡単に例外を理解することに役立つ次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="fc5db-105">The <xref:System.Exception> class has the following properties that help make understanding an exception easier.</span></span>

| <span data-ttu-id="fc5db-106">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="fc5db-106">Property Name</span></span> | <span data-ttu-id="fc5db-107">説明</span><span class="sxs-lookup"><span data-stu-id="fc5db-107">Description</span></span> |
| ------------- | ----------- |
| <xref:System.Exception.Data> | <span data-ttu-id="fc5db-108">キーと値のペアの任意のデータを保持する <xref:System.Collections.IDictionary> です。</span><span class="sxs-lookup"><span data-stu-id="fc5db-108">An <xref:System.Collections.IDictionary> that holds arbitrary data in key-value pairs.</span></span> |
| <xref:System.Exception.HelpLink> | <span data-ttu-id="fc5db-109">例外の原因に関する詳細情報を提供するヘルプ ファイルには、URL (または URN) を保持できます。</span><span class="sxs-lookup"><span data-stu-id="fc5db-109">Can hold a URL (or URN) to a help file that provides extensive information about the cause of an exception.</span></span> |
| <xref:System.Exception.InnerException> | <span data-ttu-id="fc5db-110">このプロパティを使用すると、例外処理中に一連の例外を作成して保持することができます。</span><span class="sxs-lookup"><span data-stu-id="fc5db-110">This property can be used to create and preserve a series of exceptions during exception handling.</span></span> <span data-ttu-id="fc5db-111">既にキャッチされた例外を含む新しい例外を作成するのにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="fc5db-111">You can use it to create a new exception that contains previously caught exceptions.</span></span> <span data-ttu-id="fc5db-112"><xref:System.Exception.InnerException> プロパティの 2 つ目の例外によって、元の例外をキャプチャできます。これにより、2 つ目の例外を処理するコードが追加の情報を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="fc5db-112">The original exception can be captured by the second exception in the <xref:System.Exception.InnerException> property, allowing code that handles the second exception to examine the additional information.</span></span> <span data-ttu-id="fc5db-113">たとえば、形式が正しくない引数を受け取るメソッドがあるとします。</span><span class="sxs-lookup"><span data-stu-id="fc5db-113">For example, suppose you have a method that receives an argument that's improperly formatted.</span></span>  <span data-ttu-id="fc5db-114">コードは、引数の読み取りを試みますが、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="fc5db-114">The code tries to read the argument, but an exception is thrown.</span></span> <span data-ttu-id="fc5db-115">メソッドは、例外をキャッチし、<xref:System.FormatException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="fc5db-115">The method catches the exception and throws a <xref:System.FormatException>.</span></span> <span data-ttu-id="fc5db-116">例外がスローされた原因を判断するための呼び出し元の機能を向上させるには、ヘルパー ルーチンによってスローされた例外をキャッチし、発生したエラーの内容を示す例外をスローするメソッドが望ましい場合があります。</span><span class="sxs-lookup"><span data-stu-id="fc5db-116">To improve the caller's ability to determine the reason an exception is thrown, it is sometimes desirable for a method to catch an exception thrown by a helper routine and then throw an exception more indicative of the error that has occurred.</span></span> <span data-ttu-id="fc5db-117">内部例外の参照を元の例外に設定できる、新しいより意味のある例外を作成できます。</span><span class="sxs-lookup"><span data-stu-id="fc5db-117">A new and more meaningful exception can be created, where the inner exception reference can be set to the original exception.</span></span> <span data-ttu-id="fc5db-118">この意味のある例外は、呼び出し元にスローすることができます。</span><span class="sxs-lookup"><span data-stu-id="fc5db-118">This more meaningful exception can then be thrown to the caller.</span></span> <span data-ttu-id="fc5db-119">この機能により、最初にスローされた例外で終了する一連のリンクされた例外を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="fc5db-119">Note that with this functionality, you can create a series of linked exceptions that ends with the exception that was thrown first.</span></span> |
| <xref:System.Exception.Message> | <span data-ttu-id="fc5db-120">例外の原因に関する詳細を提供します。</span><span class="sxs-lookup"><span data-stu-id="fc5db-120">Provides details about the cause of an exception.</span></span>
| <xref:System.Exception.Source> | <span data-ttu-id="fc5db-121">エラーの原因となるアプリケーションまたはオブジェクトの名前を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="fc5db-121">Gets or sets the name of the application or the object that causes the error.</span></span> |
| <xref:System.Exception.StackTrace>| <span data-ttu-id="fc5db-122">エラーが発生した場所を判断するために使用できるスタック トレースが含まれています。</span><span class="sxs-lookup"><span data-stu-id="fc5db-122">Contains a stack trace that can be used to determine where an error occurred.</span></span> <span data-ttu-id="fc5db-123">デバッグ情報が使用できる場合には、スタック トレースにソース ファイル名とプログラム行番号が記述されます。</span><span class="sxs-lookup"><span data-stu-id="fc5db-123">The stack trace includes the source file name and program line number if debugging information is available.</span></span> |

<span data-ttu-id="fc5db-124"><xref:System.Exception> から継承するほとんどのクラスは、追加メンバーを実装したり、追加の機能を提供することはありません。これらは、<xref:System.Exception> から継承するだけです。</span><span class="sxs-lookup"><span data-stu-id="fc5db-124">Most of the classes that inherit from <xref:System.Exception> do not implement additional members or provide additional functionality; they simply inherit from <xref:System.Exception>.</span></span> <span data-ttu-id="fc5db-125">そのため、例外の最も重要な情報は、例外クラスの階層、例外の名前と、例外に含まれる情報で見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="fc5db-125">Therefore, the most important information for an exception can be found in the hierarchy of exception classes, the exception name, and the information contained in the exception.</span></span>

<span data-ttu-id="fc5db-126"><xref:System.Exception> から派生したオブジェクトのみをスローし、キャッチすることをお勧めしますが、<xref:System.Object> クラスから派生したオブジェクトはすべて例外としてスローできます。</span><span class="sxs-lookup"><span data-stu-id="fc5db-126">We recommend that you throw and catch only objects that derive from <xref:System.Exception>, but you can throw any object that derives from the <xref:System.Object> class as an exception.</span></span> <span data-ttu-id="fc5db-127"><xref:System.Exception> から派生していないオブジェクトのスローとキャッチは、すべての言語ではサポートされていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="fc5db-127">Note that not all languages support throwing and catching objects that do not derive from <xref:System.Exception>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fc5db-128">参照</span><span class="sxs-lookup"><span data-stu-id="fc5db-128">See Also</span></span>  
[<span data-ttu-id="fc5db-129">例外</span><span class="sxs-lookup"><span data-stu-id="fc5db-129">Exceptions</span></span>](index.md)
