---
title: 大文字の使用規則
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ef7913a2601c3a791cb028b4074ce37b9e9421b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="capitalization-conventions"></a><span data-ttu-id="c1737-102">大文字の使用規則</span><span class="sxs-lookup"><span data-stu-id="c1737-102">Capitalization Conventions</span></span>
<span data-ttu-id="c1737-103">単純なメソッドを使用するためのこの章のレイアウトのガイドライン場合は、型、メンバー、およびパラメーターについて読みやすくする識別子を一貫して、適用されるときにします。</span><span class="sxs-lookup"><span data-stu-id="c1737-103">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>  
  
## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="c1737-104">識別子の大文字と小文字の規則</span><span class="sxs-lookup"><span data-stu-id="c1737-104">Capitalization Rules for Identifiers</span></span>  
 <span data-ttu-id="c1737-105">識別子内の単語を区別するために、識別子内の各単語の最初の文字を大文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="c1737-105">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="c1737-106">アンダー スコアは、単語を区別するために使用しないでくださいまたは識別子で任意の場所に言えば、します。</span><span class="sxs-lookup"><span data-stu-id="c1737-106">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="c1737-107">これには識別子の使用によって、識別子を大文字に変換する 2 つの適切な方法があります。</span><span class="sxs-lookup"><span data-stu-id="c1737-107">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>  
  
-   <span data-ttu-id="c1737-108">Pascal 表記を使用</span><span class="sxs-lookup"><span data-stu-id="c1737-108">PascalCasing</span></span>  
  
-   <span data-ttu-id="c1737-109">camel 表記</span><span class="sxs-lookup"><span data-stu-id="c1737-109">camelCasing</span></span>  
  
 <span data-ttu-id="c1737-110">パラメーターの名前を除いて、すべての識別子を使用する、pascal 表記を使用規則は、次の例に示すように、(2 文字の長さで経由での頭字語を含む) の各単語の最初の文字を大文字になります。</span><span class="sxs-lookup"><span data-stu-id="c1737-110">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 <span data-ttu-id="c1737-111">特殊なケースは id に、次に示すように両方の文字を大文字にする、2 文字の頭字語に。</span><span class="sxs-lookup"><span data-stu-id="c1737-111">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>  
  
 `IOStream`  
  
 <span data-ttu-id="c1737-112">パラメーター名専用に使用される、camel 表記規則は、次の例に示すように、最初の単語以外の各単語の最初の文字を大文字にします。</span><span class="sxs-lookup"><span data-stu-id="c1737-112">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="c1737-113">例に示すも camel 形式の識別子を開始する 2 文字の頭字語は小文字の両方になります。</span><span class="sxs-lookup"><span data-stu-id="c1737-113">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 <span data-ttu-id="c1737-114">**✓ しないで**すべてパブリック メンバー、種類、および名前空間の名前を複数の単語で構成される pascal 表記を使用を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1737-114">**✓ DO** use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>  
  
 <span data-ttu-id="c1737-115">**✓ しないで**パラメーター名の camel 表記を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1737-115">**✓ DO** use camelCasing for parameter names.</span></span>  
  
 <span data-ttu-id="c1737-116">次の表では、さまざまな種類の識別子の大文字と小文字の規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="c1737-116">The following table describes the capitalization rules for different types of identifiers.</span></span>  
  
|<span data-ttu-id="c1737-117">識別子</span><span class="sxs-lookup"><span data-stu-id="c1737-117">Identifier</span></span>|<span data-ttu-id="c1737-118">大文字小文字の区別</span><span class="sxs-lookup"><span data-stu-id="c1737-118">Casing</span></span>|<span data-ttu-id="c1737-119">例</span><span class="sxs-lookup"><span data-stu-id="c1737-119">Example</span></span>|  
|----------------|------------|-------------|  
|<span data-ttu-id="c1737-120">名前空間</span><span class="sxs-lookup"><span data-stu-id="c1737-120">Namespace</span></span>|<span data-ttu-id="c1737-121">Pascal</span><span class="sxs-lookup"><span data-stu-id="c1737-121">Pascal</span></span>|`namespace System.Security { ... }`|  
|<span data-ttu-id="c1737-122">型</span><span class="sxs-lookup"><span data-stu-id="c1737-122">Type</span></span>|<span data-ttu-id="c1737-123">Pascal</span><span class="sxs-lookup"><span data-stu-id="c1737-123">Pascal</span></span>|`public class StreamReader { ... }`|  
|<span data-ttu-id="c1737-124">Interface</span><span class="sxs-lookup"><span data-stu-id="c1737-124">Interface</span></span>|<span data-ttu-id="c1737-125">Pascal</span><span class="sxs-lookup"><span data-stu-id="c1737-125">Pascal</span></span>|`public interface IEnumerable { ... }`|  
|<span data-ttu-id="c1737-126">メソッド</span><span class="sxs-lookup"><span data-stu-id="c1737-126">Method</span></span>|<span data-ttu-id="c1737-127">Pascal</span><span class="sxs-lookup"><span data-stu-id="c1737-127">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|<span data-ttu-id="c1737-128">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c1737-128">Property</span></span>|<span data-ttu-id="c1737-129">Pascal</span><span class="sxs-lookup"><span data-stu-id="c1737-129">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|<span data-ttu-id="c1737-130">event</span><span class="sxs-lookup"><span data-stu-id="c1737-130">Event</span></span>|<span data-ttu-id="c1737-131">Pascal</span><span class="sxs-lookup"><span data-stu-id="c1737-131">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|<span data-ttu-id="c1737-132">フィールド</span><span class="sxs-lookup"><span data-stu-id="c1737-132">Field</span></span>|<span data-ttu-id="c1737-133">Pascal</span><span class="sxs-lookup"><span data-stu-id="c1737-133">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|<span data-ttu-id="c1737-134">列挙値</span><span class="sxs-lookup"><span data-stu-id="c1737-134">Enum value</span></span>|<span data-ttu-id="c1737-135">Pascal</span><span class="sxs-lookup"><span data-stu-id="c1737-135">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|<span data-ttu-id="c1737-136">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c1737-136">Parameter</span></span>|<span data-ttu-id="c1737-137">Camel 形式</span><span class="sxs-lookup"><span data-stu-id="c1737-137">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="c1737-138">複合語の大文字と一般的な用語</span><span class="sxs-lookup"><span data-stu-id="c1737-138">Capitalizing Compound Words and Common Terms</span></span>  
 <span data-ttu-id="c1737-139">ほとんどの複合語は、大文字と小文字の目的で 1 つの単語として扱われます。</span><span class="sxs-lookup"><span data-stu-id="c1737-139">Most compound terms are treated as single words for purposes of capitalization.</span></span>  
  
 <span data-ttu-id="c1737-140">**X しないで**いわゆる閉じたフォームの複合語内の各単語を大文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="c1737-140">**X DO NOT** capitalize each word in so-called closed-form compound words.</span></span>  
  
 <span data-ttu-id="c1737-141">これらは、エンドポイントなど、1 つの単語として書き込まれる複合語です。</span><span class="sxs-lookup"><span data-stu-id="c1737-141">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="c1737-142">大文字と小文字のガイドラインについては、目的には、1 つの単語として閉じられた形式の複合語を扱います。</span><span class="sxs-lookup"><span data-stu-id="c1737-142">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="c1737-143">現在のディクショナリを使用すると、複合語が閉じたフォームで記述されたかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="c1737-143">Use a current dictionary to determine if a compound word is written in closed form.</span></span>  
  
|<span data-ttu-id="c1737-144">Pascal</span><span class="sxs-lookup"><span data-stu-id="c1737-144">Pascal</span></span>|<span data-ttu-id="c1737-145">Camel 形式</span><span class="sxs-lookup"><span data-stu-id="c1737-145">Camel</span></span>|<span data-ttu-id="c1737-146">Not</span><span class="sxs-lookup"><span data-stu-id="c1737-146">Not</span></span>|  
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
  
## <a name="case-sensitivity"></a><span data-ttu-id="c1737-147">大文字と小文字の区別</span><span class="sxs-lookup"><span data-stu-id="c1737-147">Case Sensitivity</span></span>  
 <span data-ttu-id="c1737-148">CLR で実行できる言語は、いくつかが、大文字小文字の区別をサポートする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c1737-148">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="c1737-149">でも使用する言語でサポートされる場合、その他の言語、フレームワークにアクセスする必要ありません。</span><span class="sxs-lookup"><span data-stu-id="c1737-149">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="c1737-150">したがって、外部からアクセス可能であるすべての Api は、場合、同じコンテキストで 2 つの名前を区別するために単独で使用できません。</span><span class="sxs-lookup"><span data-stu-id="c1737-150">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>  
  
 <span data-ttu-id="c1737-151">**X しないで**すべてのプログラミング言語が大文字小文字を区別があると仮定します。</span><span class="sxs-lookup"><span data-stu-id="c1737-151">**X DO NOT** assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="c1737-152">しかし、そうではありません。</span><span class="sxs-lookup"><span data-stu-id="c1737-152">They are not.</span></span> <span data-ttu-id="c1737-153">名前は、大文字と小文字だけでは区別できません。</span><span class="sxs-lookup"><span data-stu-id="c1737-153">Names cannot differ by case alone.</span></span>  
  
 <span data-ttu-id="c1737-154">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="c1737-154">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="c1737-155">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="c1737-155">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1737-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1737-156">See Also</span></span>  
 [<span data-ttu-id="c1737-157">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="c1737-157">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="c1737-158">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="c1737-158">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
