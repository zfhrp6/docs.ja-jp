---
title: "大文字の使用規則"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1bddb7bb3559e6f39b7884b92f64bee8fbb3510
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="capitalization-conventions"></a><span data-ttu-id="b5c00-102">大文字の使用規則</span><span class="sxs-lookup"><span data-stu-id="b5c00-102">Capitalization Conventions</span></span>
<span data-ttu-id="b5c00-103">単純なメソッドを使用するためのこの章のレイアウトのガイドライン場合は、型、メンバー、およびパラメーターについて読みやすくする識別子を一貫して、適用されるときにします。</span><span class="sxs-lookup"><span data-stu-id="b5c00-103">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>  
  
## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="b5c00-104">識別子の大文字と小文字の規則</span><span class="sxs-lookup"><span data-stu-id="b5c00-104">Capitalization Rules for Identifiers</span></span>  
 <span data-ttu-id="b5c00-105">識別子内の単語を区別するために、識別子内の各単語の最初の文字を大文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="b5c00-105">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="b5c00-106">アンダー スコアは、単語を区別するために使用しないでくださいまたは識別子で任意の場所に言えば、します。</span><span class="sxs-lookup"><span data-stu-id="b5c00-106">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="b5c00-107">これには識別子の使用によって、識別子を大文字に変換する 2 つの適切な方法があります。</span><span class="sxs-lookup"><span data-stu-id="b5c00-107">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>  
  
-   <span data-ttu-id="b5c00-108">Pascal 表記を使用</span><span class="sxs-lookup"><span data-stu-id="b5c00-108">PascalCasing</span></span>  
  
-   <span data-ttu-id="b5c00-109">camel 表記</span><span class="sxs-lookup"><span data-stu-id="b5c00-109">camelCasing</span></span>  
  
 <span data-ttu-id="b5c00-110">パラメーターの名前を除いて、すべての識別子を使用する、pascal 表記を使用規則は、次の例に示すように、(2 文字の長さで経由での頭字語を含む) の各単語の最初の文字を大文字になります。</span><span class="sxs-lookup"><span data-stu-id="b5c00-110">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 <span data-ttu-id="b5c00-111">特殊なケースは id に、次に示すように両方の文字を大文字にする、2 文字の頭字語に。</span><span class="sxs-lookup"><span data-stu-id="b5c00-111">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>  
  
 `IOStream`  
  
 <span data-ttu-id="b5c00-112">パラメーター名専用に使用される、camel 表記規則は、次の例に示すように、最初の単語以外の各単語の最初の文字を大文字にします。</span><span class="sxs-lookup"><span data-stu-id="b5c00-112">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="b5c00-113">例に示すも camel 形式の識別子を開始する 2 文字の頭字語は小文字の両方になります。</span><span class="sxs-lookup"><span data-stu-id="b5c00-113">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 <span data-ttu-id="b5c00-114">**✓ しないで**すべてパブリック メンバー、種類、および名前空間の名前を複数の単語で構成される pascal 表記を使用を使用します。</span><span class="sxs-lookup"><span data-stu-id="b5c00-114">**✓ DO** use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>  
  
 <span data-ttu-id="b5c00-115">**✓ しないで**パラメーター名の camel 表記を使用します。</span><span class="sxs-lookup"><span data-stu-id="b5c00-115">**✓ DO** use camelCasing for parameter names.</span></span>  
  
 <span data-ttu-id="b5c00-116">次の表では、さまざまな種類の識別子の大文字と小文字の規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="b5c00-116">The following table describes the capitalization rules for different types of identifiers.</span></span>  
  
|<span data-ttu-id="b5c00-117">識別子</span><span class="sxs-lookup"><span data-stu-id="b5c00-117">Identifier</span></span>|<span data-ttu-id="b5c00-118">大文字小文字の区別</span><span class="sxs-lookup"><span data-stu-id="b5c00-118">Casing</span></span>|<span data-ttu-id="b5c00-119">例</span><span class="sxs-lookup"><span data-stu-id="b5c00-119">Example</span></span>|  
|----------------|------------|-------------|  
|<span data-ttu-id="b5c00-120">名前空間</span><span class="sxs-lookup"><span data-stu-id="b5c00-120">Namespace</span></span>|<span data-ttu-id="b5c00-121">Pascal</span><span class="sxs-lookup"><span data-stu-id="b5c00-121">Pascal</span></span>|`namespace System.Security { ... }`|  
|<span data-ttu-id="b5c00-122">型</span><span class="sxs-lookup"><span data-stu-id="b5c00-122">Type</span></span>|<span data-ttu-id="b5c00-123">Pascal</span><span class="sxs-lookup"><span data-stu-id="b5c00-123">Pascal</span></span>|`public class StreamReader { ... }`|  
|<span data-ttu-id="b5c00-124">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b5c00-124">Interface</span></span>|<span data-ttu-id="b5c00-125">Pascal</span><span class="sxs-lookup"><span data-stu-id="b5c00-125">Pascal</span></span>|`public interface IEnumerable { ... }`|  
|<span data-ttu-id="b5c00-126">メソッド</span><span class="sxs-lookup"><span data-stu-id="b5c00-126">Method</span></span>|<span data-ttu-id="b5c00-127">Pascal</span><span class="sxs-lookup"><span data-stu-id="b5c00-127">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|<span data-ttu-id="b5c00-128">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b5c00-128">Property</span></span>|<span data-ttu-id="b5c00-129">Pascal</span><span class="sxs-lookup"><span data-stu-id="b5c00-129">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|<span data-ttu-id="b5c00-130">イベント</span><span class="sxs-lookup"><span data-stu-id="b5c00-130">Event</span></span>|<span data-ttu-id="b5c00-131">Pascal</span><span class="sxs-lookup"><span data-stu-id="b5c00-131">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|<span data-ttu-id="b5c00-132">フィールド</span><span class="sxs-lookup"><span data-stu-id="b5c00-132">Field</span></span>|<span data-ttu-id="b5c00-133">Pascal</span><span class="sxs-lookup"><span data-stu-id="b5c00-133">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|<span data-ttu-id="b5c00-134">列挙値</span><span class="sxs-lookup"><span data-stu-id="b5c00-134">Enum value</span></span>|<span data-ttu-id="b5c00-135">Pascal</span><span class="sxs-lookup"><span data-stu-id="b5c00-135">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|<span data-ttu-id="b5c00-136">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b5c00-136">Parameter</span></span>|<span data-ttu-id="b5c00-137">Camel 形式</span><span class="sxs-lookup"><span data-stu-id="b5c00-137">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="b5c00-138">複合語の大文字と一般的な用語</span><span class="sxs-lookup"><span data-stu-id="b5c00-138">Capitalizing Compound Words and Common Terms</span></span>  
 <span data-ttu-id="b5c00-139">ほとんどの複合語は、大文字と小文字の目的で 1 つの単語として扱われます。</span><span class="sxs-lookup"><span data-stu-id="b5c00-139">Most compound terms are treated as single words for purposes of capitalization.</span></span>  
  
 <span data-ttu-id="b5c00-140">**X しないで**いわゆる閉じたフォームの複合語内の各単語を大文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="b5c00-140">**X DO NOT** capitalize each word in so-called closed-form compound words.</span></span>  
  
 <span data-ttu-id="b5c00-141">これらは、エンドポイントなど、1 つの単語として書き込まれる複合語です。</span><span class="sxs-lookup"><span data-stu-id="b5c00-141">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="b5c00-142">大文字と小文字のガイドラインについては、目的には、1 つの単語として閉じられた形式の複合語を扱います。</span><span class="sxs-lookup"><span data-stu-id="b5c00-142">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="b5c00-143">現在のディクショナリを使用すると、複合語が閉じたフォームで記述されたかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="b5c00-143">Use a current dictionary to determine if a compound word is written in closed form.</span></span>  
  
|<span data-ttu-id="b5c00-144">Pascal</span><span class="sxs-lookup"><span data-stu-id="b5c00-144">Pascal</span></span>|<span data-ttu-id="b5c00-145">Camel 形式</span><span class="sxs-lookup"><span data-stu-id="b5c00-145">Camel</span></span>|<span data-ttu-id="b5c00-146">Not</span><span class="sxs-lookup"><span data-stu-id="b5c00-146">Not</span></span>|  
|------------|-----------|---------|  
|`BitFlag`|`bitFlag`|`Bitflag`|  
|`Callback`|`callback`|`CallBack`|  
|`Canceled`|`canceled`|`Cancelled`|  
|`DoNot`|`doNot`|`Don't`|  
|`Email`|`email`|`EMail`|  
|`Endpoint`|`endpoint`|`EndPoint`|  
|`FileName`|`fileName`|`Filename`|  
|`Gridline`|`gridline`|`GridLine`|  
|`Hashtable`|`hashtable`|`HashTable`|  
|`Id`|`id`|`ID`|  
|`Indexes`|`indexes`|`Indices`|  
|`LogOff`|`logOff`|`LogOut`|  
|`LogOn`|`logOn`|`LogIn`|  
|`Metadata`|`metadata`|`MetaData, metaData`|  
|`Multipanel`|`multipanel`|`MultiPanel`|  
|`Multiview`|`multiview`|`MultiView`|  
|`Namespace`|`namespace`|`NameSpace`|  
|`Ok`|`ok`|`OK`|  
|`Pi`|`pi`|`PI`|  
|`Placeholder`|`placeholder`|`PlaceHolder`|  
|`SignIn`|`signIn`|`SignOn`|  
|`SignOut`|`signOut`|`SignOff`|  
|`UserName`|`userName`|`Username`|  
|`WhiteSpace`|`whiteSpace`|`Whitespace`|  
|`Writable`|`writable`|`Writeable`|  
  
## <a name="case-sensitivity"></a><span data-ttu-id="b5c00-147">大文字と小文字の区別</span><span class="sxs-lookup"><span data-stu-id="b5c00-147">Case Sensitivity</span></span>  
 <span data-ttu-id="b5c00-148">CLR で実行できる言語は、いくつかが、大文字小文字の区別をサポートする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b5c00-148">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="b5c00-149">でも使用する言語でサポートされる場合、その他の言語、フレームワークにアクセスする必要ありません。</span><span class="sxs-lookup"><span data-stu-id="b5c00-149">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="b5c00-150">したがって、外部からアクセス可能であるすべての Api は、場合、同じコンテキストで 2 つの名前を区別するために単独で使用できません。</span><span class="sxs-lookup"><span data-stu-id="b5c00-150">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>  
  
 <span data-ttu-id="b5c00-151">**X しないで**すべてのプログラミング言語が大文字小文字を区別があると仮定します。</span><span class="sxs-lookup"><span data-stu-id="b5c00-151">**X DO NOT** assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="b5c00-152">しかし、そうではありません。</span><span class="sxs-lookup"><span data-stu-id="b5c00-152">They are not.</span></span> <span data-ttu-id="b5c00-153">名前は、大文字と小文字だけでは区別できません。</span><span class="sxs-lookup"><span data-stu-id="b5c00-153">Names cannot differ by case alone.</span></span>  
  
 <span data-ttu-id="b5c00-154">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="b5c00-154">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b5c00-155">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="b5c00-155">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5c00-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5c00-156">See Also</span></span>  
 [<span data-ttu-id="b5c00-157">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="b5c00-157">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="b5c00-158">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="b5c00-158">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
