---
title: シールされていないクラス
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 672d36c6b888ee9a89a76d5d417a7a7e92dd8f36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="unsealed-classes"></a><span data-ttu-id="1e000-102">シールされていないクラス</span><span class="sxs-lookup"><span data-stu-id="1e000-102">Unsealed Classes</span></span>
<span data-ttu-id="1e000-103">シール クラスは継承できませんし、機能拡張するを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="1e000-103">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="1e000-104">これに対し、封印されていないクラスから継承できるクラスと呼びます。</span><span class="sxs-lookup"><span data-stu-id="1e000-104">In contrast, classes that can be inherited from are called unsealed classes.</span></span>  
  
 <span data-ttu-id="1e000-105">**✓ を検討してください**安価なを提供するのにまだ高く評価されたフレームワークを拡張機能として、仮想またはプロテクト メンバーを追加なしで封印されていないクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="1e000-105">**✓ CONSIDER** using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>  
  
 <span data-ttu-id="1e000-106">多くの場合、開発者はカスタム コンス トラクター、新しいメソッド、またはメソッドのオーバー ロードなどの便利なメンバーを追加するために、封印されていないクラスから継承したいと考えているとします。</span><span class="sxs-lookup"><span data-stu-id="1e000-106">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="1e000-107">たとえば、`System.Messaging.MessageQueue`が封印されていないとできるので、ユーザーのキューを作成するカスタムな特定のキューのパスにその既定値または特定のシナリオ用の API を簡略化するカスタム メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="1e000-107">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>  
  
 <span data-ttu-id="1e000-108">既定ではほとんどのプログラミング言語でクラスが封印されていないし、これも推奨される既定のフレームワークのほとんどのクラス。</span><span class="sxs-lookup"><span data-stu-id="1e000-108">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="1e000-109">Unsealed 型によって提供される機能拡張は、フレームワークのユーザーがかなり歓迎いたし、unsealed 型に関連付けられているテストの比較的低コストのために提供する非常に低コストです。</span><span class="sxs-lookup"><span data-stu-id="1e000-109">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>  
  
 <span data-ttu-id="1e000-110">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="1e000-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="1e000-111">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="1e000-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e000-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e000-112">See Also</span></span>  
 [<span data-ttu-id="1e000-113">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="1e000-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="1e000-114">機能拡張のデザイン</span><span class="sxs-lookup"><span data-stu-id="1e000-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [<span data-ttu-id="1e000-115">シール</span><span class="sxs-lookup"><span data-stu-id="1e000-115">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)
