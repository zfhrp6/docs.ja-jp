---
title: "基本的な文字列操作"
description: "基本的な文字列操作"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 9658098d-de60-4868-ba5b-0c278748a90f
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: b8bdbeccd226c412e725200fcaf81ec568afc5bc
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="basic-string-operations"></a><span data-ttu-id="d3624-104">基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="d3624-104">Basic string operations</span></span>

<span data-ttu-id="d3624-105">アプリケーションは、多くの場合、ユーザー入力に基づいてメッセージを構築することによってユーザーに応答します。</span><span class="sxs-lookup"><span data-stu-id="d3624-105">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="d3624-106">たとえば、Web サイトで、新たにログオンしたユーザーに対して、ユーザーの名前を含む特別なメッセージで応答することは珍しいことではありません。</span><span class="sxs-lookup"><span data-stu-id="d3624-106">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="d3624-107">[System.String](xref:System.String) と [System.Text.StringBuilder](xref:System.Text.StringBuilder) クラスのいくつかのメソッドを使用すると、ユーザー インターフェイスに表示するカスタム文字列を動的に構築できます。</span><span class="sxs-lookup"><span data-stu-id="d3624-107">Several methods in the [System.String](xref:System.String) and [System.Text.StringBuilder](xref:System.Text.StringBuilder) classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="d3624-108">これらのメソッドでは、バイト配列から新しい文字列を作成する、文字列の値を比較する、既存の文字列を変更するなどのいくつかの基本的な文字列操作を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="d3624-108">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d3624-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d3624-109">In This Section</span></span>

<span data-ttu-id="d3624-110">[新しい文字列の作成](creating-new.md) - オブジェクトを文字列に変換し、文字列を結合する基本的な方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3624-110">[Creating new strings](creating-new.md) - Describes basic ways to convert objects into strings and to combine strings.</span></span>

<span data-ttu-id="d3624-111">[文字のトリムと削除](trimming.md) - 文字列内の文字をトリミングまたは削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3624-111">[Trimming and removing characters](trimming.md) - Describes how to trim or remove characters in a string.</span></span> 

<span data-ttu-id="d3624-112">[文字列の埋め込み](padding.md) - 文字列に文字または空白を挿入する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3624-112">[Padding strings](padding.md) - Describes how to insert characters or empty spaces into a string.</span></span>

<span data-ttu-id="d3624-113">[文字列の比較](comparing.md) -2 つ以上の文字列の内容を比較する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3624-113">[Comparing strings](comparing.md) - Describes how to compare the contents of two or more strings.</span></span>

<span data-ttu-id="d3624-114">[大文字と小文字の変更](changing-case.md) - 文字列内の文字の大文字と小文字を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3624-114">[Changing case](changing-case.md) - Describes how to change the case of characters within a string.</span></span>

<span data-ttu-id="d3624-115">[StringBuilder クラスの使用](stringbuilder.md) - [StringBuilder](xref:System.Text.StringBuilder) クラスを使用して、動的な文字列オブジェクトを作成して変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3624-115">[Using the StringBuilder class](stringbuilder.md) - Describes how to create and modify dynamic string objects with the [StringBuilder](xref:System.Text.StringBuilder) class.</span></span>

<span data-ttu-id="d3624-116">[方法: 基本的な文字列操作を実行する](basic-manipulations.md) - 基本的な文字列操作の使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="d3624-116">[How to: Perform basic string manipulations](basic-manipulations.md) - Demonstrates the use of basic string operations.</span></span>

## <a name="related-sections"></a><span data-ttu-id="d3624-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3624-117">Related Sections</span></span>

<span data-ttu-id="d3624-118">[型変換](type-conversion.md) - 型を変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3624-118">[Type conversion](type-conversion.md) - Describes how to convert from one type to another.</span></span>

<span data-ttu-id="d3624-119">[型の書式設定](formatting-types.md) - 文字列の書式指定子を使用して文字列の書式を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3624-119">[Formatting types](formatting-types.md) - Describes how to format strings using the string format specifiers.</span></span>



