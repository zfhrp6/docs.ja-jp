---
title: ".NET Framework での基本的な文字列操作"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f241b99f97cad081a65fd8654169e444a1b588cb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="15e78-102">.NET での基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="15e78-102">Basic String Operations in .NET</span></span>
<span data-ttu-id="15e78-103">アプリケーションは、多くの場合、ユーザー入力に基づいてメッセージを構築することによってユーザーに応答します。</span><span class="sxs-lookup"><span data-stu-id="15e78-103">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="15e78-104">たとえば、Web サイトで、新たにログオンしたユーザーに対して、ユーザーの名前を含む特別なメッセージで応答することは珍しいことではありません。</span><span class="sxs-lookup"><span data-stu-id="15e78-104">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="15e78-105">いくつかのメソッド、<xref:System.String?displayProperty=nameWithType>と<xref:System.Text.StringBuilder?displayProperty=nameWithType>クラスを使用すると、ユーザー インターフェイスに表示するカスタムの文字列を動的に構築します。</span><span class="sxs-lookup"><span data-stu-id="15e78-105">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="15e78-106">これらのメソッドでは、バイト配列から新しい文字列を作成する、文字列の値を比較する、既存の文字列を変更するなどのいくつかの基本的な文字列操作を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="15e78-106">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="15e78-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="15e78-107">In This Section</span></span>  
 [<span data-ttu-id="15e78-108">新しい文字列の作成</span><span class="sxs-lookup"><span data-stu-id="15e78-108">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="15e78-109">オブジェクトを文字列に変換し、文字列を結合するための基本的な方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="15e78-109">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="15e78-110">文字のトリムと削除</span><span class="sxs-lookup"><span data-stu-id="15e78-110">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="15e78-111">トリミングまたは文字列の文字を削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="15e78-111">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="15e78-112">文字列の埋め込み</span><span class="sxs-lookup"><span data-stu-id="15e78-112">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="15e78-113">文字列に文字または空白を挿入する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="15e78-113">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="15e78-114">文字列の比較</span><span class="sxs-lookup"><span data-stu-id="15e78-114">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="15e78-115">2 つ以上の文字列の内容を比較する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="15e78-115">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="15e78-116">大文字と小文字の変更</span><span class="sxs-lookup"><span data-stu-id="15e78-116">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="15e78-117">文字列内の文字の大文字と小文字を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="15e78-117">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="15e78-118">StringBuilder クラスの使用</span><span class="sxs-lookup"><span data-stu-id="15e78-118">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="15e78-119">文字列を動的オブジェクトを作成および変更方法について説明します、<xref:System.Text.StringBuilder>クラスです。</span><span class="sxs-lookup"><span data-stu-id="15e78-119">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="15e78-120">方法: 基本的な文字列操作を実行する</span><span class="sxs-lookup"><span data-stu-id="15e78-120">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="15e78-121">基本的な文字列操作の使用を示します。</span><span class="sxs-lookup"><span data-stu-id="15e78-121">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="15e78-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="15e78-122">Related Sections</span></span>  
 [<span data-ttu-id="15e78-123">.NET での型変換</span><span class="sxs-lookup"><span data-stu-id="15e78-123">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="15e78-124">1 つの型を別の型に変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="15e78-124">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="15e78-125">型の書式設定</span><span class="sxs-lookup"><span data-stu-id="15e78-125">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="15e78-126">書式指定子を使用して文字列を書式設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="15e78-126">Describes how to format strings using format specifiers.</span></span>
