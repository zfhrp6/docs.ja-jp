---
title: 型のメンバーの名前
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25fe93b63c518f54ee72300f26dfcb3f3ad21d76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575350"
---
# <a name="names-of-type-members"></a><span data-ttu-id="9ce8b-102">型のメンバーの名前</span><span class="sxs-lookup"><span data-stu-id="9ce8b-102">Names of Type Members</span></span>
<span data-ttu-id="9ce8b-103">メンバーの種類がされています: メソッド、プロパティ、イベント、コンス トラクター、およびフィールドです。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="9ce8b-104">次のセクションでは、型のメンバーの名前付けのガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-104">The following sections describe guidelines for naming type members.</span></span>  
  
## <a name="names-of-methods"></a><span data-ttu-id="9ce8b-105">メソッドの名前</span><span class="sxs-lookup"><span data-stu-id="9ce8b-105">Names of Methods</span></span>  
 <span data-ttu-id="9ce8b-106">メソッドは操作を実行する手段であるため、デザインのガイドラインは、動詞または動詞句メソッド名にすることが必要です。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="9ce8b-107">このガイドラインにも従うプロパティと型名を名詞または形容詞句からメソッド名を区別するために機能します。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>  
  
 <span data-ttu-id="9ce8b-108">**✓ しないで**動詞または動詞句は、メソッドの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-108">**✓ DO** give methods names that are verbs or verb phrases.</span></span>  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a><span data-ttu-id="9ce8b-109">プロパティの名前</span><span class="sxs-lookup"><span data-stu-id="9ce8b-109">Names of Properties</span></span>  
 <span data-ttu-id="9ce8b-110">他のメンバーとは異なり名詞句または形容詞名に、プロパティを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="9ce8b-111">プロパティが、データを参照し、プロパティの名前を反映するためです。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="9ce8b-112">プロパティ名は、pascal 表記を使用が常に使用されます。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-112">PascalCasing is always used for property names.</span></span>  
  
 <span data-ttu-id="9ce8b-113">**✓ しないで**名詞、名詞句、または形容詞を使用してプロパティの名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-113">**✓ DO** name properties using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="9ce8b-114">**X しないで**次の例のように、"Get"メソッドの名前に一致するプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-114">**X DO NOT** have properties that match the name of "Get" methods as in the following example:</span></span>  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 <span data-ttu-id="9ce8b-115">このパターンでは、通常、プロパティがメソッドを実際にする必要がありますを示します。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-115">This pattern typically indicates that the property should really be a method.</span></span>  
  
 <span data-ttu-id="9ce8b-116">**✓ しないで**後に"List"または"Collection"単数形の語句を使用する代わりに、コレクション内の項目を記述する複数形の語句でコレクションのプロパティの名前を付けます</span><span class="sxs-lookup"><span data-stu-id="9ce8b-116">**✓ DO** name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection."</span></span>  
  
 <span data-ttu-id="9ce8b-117">**✓ しないで**肯定の語句でブール型プロパティの名前 (`CanSeek`の代わりに`CantSeek`)。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-117">**✓ DO** name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="9ce8b-118">ブール型プロパティもプレフィックスを必要に応じて、"Is"と"、"したり"は、"値を追加する場合に限定します。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-118">Optionally, you can also prefix Boolean properties with "Is," "Can," or "Has," but only where it adds value.</span></span>  
  
 <span data-ttu-id="9ce8b-119">**✓ を検討してください**プロパティの型と同じ名前を提供します。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-119">**✓ CONSIDER** giving a property the same name as its type.</span></span>  
  
 <span data-ttu-id="9ce8b-120">たとえば、次のプロパティ正しく取得および設定という名前列挙値`Color`ので、プロパティの名前が`Color`:</span><span class="sxs-lookup"><span data-stu-id="9ce8b-120">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a><span data-ttu-id="9ce8b-121">イベントの名前</span><span class="sxs-lookup"><span data-stu-id="9ce8b-121">Names of Events</span></span>  
 <span data-ttu-id="9ce8b-122">イベントは、常に、何らかのアクションでは、いずれかの問題であるかが発生した 1 つを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-122">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="9ce8b-123">そのため、メソッド、イベント名前付けには、動詞と同様動詞の時制を使用するイベントが発生した時刻を指定します。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-123">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>  
  
 <span data-ttu-id="9ce8b-124">**✓ しないで**動詞または動詞句を持つイベントの名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-124">**✓ DO** name events with a verb or a verb phrase.</span></span>  
  
 <span data-ttu-id="9ce8b-125">例としては、 `Clicked`、 `Painting`、`DroppedDown`のようにします。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-125">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>  
  
 <span data-ttu-id="9ce8b-126">**✓ しないで**名前を指定してイベントの概念で前に、と後、現在および過去時制を使用します。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-126">**✓ DO** give events names with a concept of before and after, using the present and past tenses.</span></span>  
  
 <span data-ttu-id="9ce8b-127">たとえば、クローズ イベントには、ウィンドウが閉じられる前に発生が呼び出されます`Closing`、ウィンドウが閉じられた後に発生する 1 つが呼び出されますと`Closed`です。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-127">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>  
  
 <span data-ttu-id="9ce8b-128">**X しないで**"Before"または"After"プレフィックスまたは postfixes を示す前と後イベントを使用します。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-128">**X DO NOT** use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="9ce8b-129">現在使用して上記の過去時制。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-129">Use present and past tenses as just described.</span></span>  
  
 <span data-ttu-id="9ce8b-130">**✓ しないで**"EventHandler"サフィックスを持つイベント ハンドラー (デリゲートがイベントの種類として使用) という名前を次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-130">**✓ DO** name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 <span data-ttu-id="9ce8b-131">**✓ は**という 2 つのパラメーターを使用して`sender`と`e`イベント ハンドラーにおいてです。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-131">**✓ DO** use two parameters named `sender` and `e` in event handlers.</span></span>  
  
 <span data-ttu-id="9ce8b-132">送信元のパラメーターは、イベントを発生させたオブジェクトを表します。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-132">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="9ce8b-133">型の送信元のパラメーターは、通常`object`場合より具体的な種類を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-133">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>  
  
 <span data-ttu-id="9ce8b-134">**✓ しないで**イベント引数クラス"EventArgs"サフィックスを持つ名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-134">**✓ DO** name event argument classes with the "EventArgs" suffix.</span></span>  
  
## <a name="names-of-fields"></a><span data-ttu-id="9ce8b-135">フィールドの名前</span><span class="sxs-lookup"><span data-stu-id="9ce8b-135">Names of Fields</span></span>  
 <span data-ttu-id="9ce8b-136">フィールドの名前付けのガイドラインは、パブリックおよびプロテクトの静的フィールドに適用します。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-136">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="9ce8b-137">内部およびプライベート フィールドが、ガイドラインで対応されていないと、パブリックまたはプロテクトのインスタンス フィールドがによって許可されていません、[メンバー デザインのガイドライン](../../../docs/standard/design-guidelines/member.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-137">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](../../../docs/standard/design-guidelines/member.md).</span></span>  
  
 <span data-ttu-id="9ce8b-138">**✓ しないで**フィールドの名前で pascal 表記を使用を使用します。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-138">**✓ DO** use PascalCasing in field names.</span></span>  
  
 <span data-ttu-id="9ce8b-139">**✓ しないで**名詞、名詞句、または形容詞を使用してフィールドの名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-139">**✓ DO** name fields using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="9ce8b-140">**X しないで**フィールド名にプレフィックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-140">**X DO NOT** use a prefix for field names.</span></span>  
  
 <span data-ttu-id="9ce8b-141">たとえば、使わない g「_」または「s _」を静的フィールドを示します。</span><span class="sxs-lookup"><span data-stu-id="9ce8b-141">For example, do not use "g_" or "s_" to indicate static fields.</span></span>  
  
 <span data-ttu-id="9ce8b-142">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="9ce8b-142">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9ce8b-143">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="9ce8b-143">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ce8b-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ce8b-144">See Also</span></span>  
 [<span data-ttu-id="9ce8b-145">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="9ce8b-145">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="9ce8b-146">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="9ce8b-146">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
