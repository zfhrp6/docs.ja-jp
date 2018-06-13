---
title: セキュリティとパブリックの読み取り専用配列フィールド
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0110bb42775d8a5df9ca268b35db3abaffec84f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392630"
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="17a49-102">セキュリティとパブリックの読み取り専用配列フィールド</span><span class="sxs-lookup"><span data-stu-id="17a49-102">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="17a49-103">読み取り専用のパブリック配列フィールドを変更できるため、境界の動作や、アプリケーションのセキュリティを定義するのには、マネージ ライブラリからの読み取り専用のパブリック配列フィールドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="17a49-103">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17a49-104">コメント</span><span class="sxs-lookup"><span data-stu-id="17a49-104">Remarks</span></span>  
 <span data-ttu-id="17a49-105">.NET framework の一部のクラスには、プラットフォーム固有の境界パラメーターが含まれている読み取り専用のパブリック フィールドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="17a49-105">Some .NET framework classes include read-only public fields that contain platform-specific boundary parameters.</span></span>  <span data-ttu-id="17a49-106">たとえば、<xref:System.IO.Path.InvalidPathChars>フィールドは、ファイルのパス文字列の許可されていない文字を表す配列。</span><span class="sxs-lookup"><span data-stu-id="17a49-106">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span>  <span data-ttu-id="17a49-107">多くの同様のフィールドは、.NET Framework 全体にわたって存在します。</span><span class="sxs-lookup"><span data-stu-id="17a49-107">Many similar fields are present throughout the .NET Framework.</span></span>  
  
 <span data-ttu-id="17a49-108">パブリックの読み取り専用フィールドの値と同様に<xref:System.IO.Path.InvalidPathChars>コードや、コードのアプリケーション ドメインを共有しているコードで変更できます。</span><span class="sxs-lookup"><span data-stu-id="17a49-108">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="17a49-109">アプリケーションの境界の動作を定義するのに次のようにパブリックの読み取り専用の配列フィールドを使用する必要がありますできません。</span><span class="sxs-lookup"><span data-stu-id="17a49-109">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="17a49-110">作成する場合は、悪意のあるコードは境界の定義を変更し、予期しない方法でコードを利用できます。</span><span class="sxs-lookup"><span data-stu-id="17a49-110">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="17a49-111">2.0 と .NET Framework の以降のバージョンでは、パブリックの配列フィールドを使用する代わりに新しい配列を返すメソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="17a49-111">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="17a49-112">使用せずになど、<xref:System.IO.Path.InvalidPathChars>フィールドを使用してください、<xref:System.IO.Path.GetInvalidPathChars%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="17a49-112">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="17a49-113">.NET Framework の型が内部的には境界の種類を定義するパブリック フィールドを使用しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="17a49-113">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="17a49-114">代わりに、.NET Framework では、別のプライベート フィールドを使用します。</span><span class="sxs-lookup"><span data-stu-id="17a49-114">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="17a49-115">これらのパブリック フィールドの値を変更しても、.NET Framework の型の動作は変わりません。</span><span class="sxs-lookup"><span data-stu-id="17a49-115">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17a49-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="17a49-116">See Also</span></span>  
 [<span data-ttu-id="17a49-117">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="17a49-117">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
