---
title: "レコード長が正しくありません。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 747d62cb41ef841b4486e0c7108c37a86929683e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="bad-record-length"></a><span data-ttu-id="7af75-102">レコード長が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="7af75-102">Bad record length</span></span>
<span data-ttu-id="7af75-103">このエラーでは以下の原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="7af75-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="7af75-104">指定されたレコードの変数の長さ、 `FileGet`、 `FileGetObject`、`FilePut`または`FilePutObject`ステートメントは、対応する指定された長さによって異なります。`FileOpen`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="7af75-104">The length of a record variable specified in a `FileGet`, `FileGetObject`, `FilePut` or `FilePutObject` statement differs from the length specified in the corresponding `FileOpen` statement.</span></span>  
  
-   <span data-ttu-id="7af75-105">内の変数、`FilePut`または`FilePutObject`ステートメントまたは可変長文字列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7af75-105">The variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string.</span></span>  
  
-   <span data-ttu-id="7af75-106">内の変数、`FilePut`または`FilePutObject`かが含まれています、`Variant`型です。</span><span class="sxs-lookup"><span data-stu-id="7af75-106">The variable in a `FilePut` or `FilePutObject` is or includes a `Variant` type.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7af75-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="7af75-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="7af75-108">レコードの変数の型を定義するユーザー定義型の固定長変数のサイズの合計と同じでは、値に記載されていることを確認、`FileOpen`ステートメントの`Len`句。</span><span class="sxs-lookup"><span data-stu-id="7af75-108">Make sure the sum of the sizes of fixed-length variables in the user-defined type defining the record variable's type is the same as the value stated in the `FileOpen` statement's `Len` clause.</span></span>  
  
2.  <span data-ttu-id="7af75-109">場合内の変数、`FilePut`または`FilePutObject`可変長文字列は、少なくとも 2 文字で指定されたレコードの長さよりも短いかどうかを確認、ステートメントが可変長文字列が含まれていますか、`Len`の句、 `FileOpen`ステートメント。</span><span class="sxs-lookup"><span data-stu-id="7af75-109">If the variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string, make sure the variable-length string is at least 2 characters shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
3.  <span data-ttu-id="7af75-110">場合内の変数、`FilePut`または`FilePutObject`かが含まれています、`Variant`可変長の文字列は、少なくとも 4 バイトで指定されたレコードの長さよりも短いかどうかを確認、`Len`の句、`FileOpen`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="7af75-110">If the variable in a `FilePut` or `FilePutObject` is or includes a `Variant` make sure the variable-length string is at least 4 bytes shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7af75-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="7af75-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
