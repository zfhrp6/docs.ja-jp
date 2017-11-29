---
title: "正しくないパターン文字列"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f824a5844d6d2b365358030119826266a4b42ef3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="28053-102">正しくないパターン文字列</span><span class="sxs-lookup"><span data-stu-id="28053-102">Invalid pattern string</span></span>
<span data-ttu-id="28053-103">検索の `Like` 演算で指定されているパターン文字列が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="28053-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="28053-104">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="28053-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="28053-105">リスト式に使用できる文字を確認します。</span><span class="sxs-lookup"><span data-stu-id="28053-105">Review the valid characters for list expressions.</span></span>  
  
2.  <span data-ttu-id="28053-106">パターン範囲の指定で、 `[a-z]`のように、範囲の開始文字が終了文字より小さいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="28053-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3.  <span data-ttu-id="28053-107">パターン範囲の指定で、 `[a--z]`のように、複数のハイフンが続けて指定されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="28053-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4.  <span data-ttu-id="28053-108">パターン範囲を右角かっこで終了します。</span><span class="sxs-lookup"><span data-stu-id="28053-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28053-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="28053-109">See Also</span></span>  
 [<span data-ttu-id="28053-110">Like 演算子</span><span class="sxs-lookup"><span data-stu-id="28053-110">Like Operator</span></span>](../../visual-basic/language-reference/operators/like-operator.md)
