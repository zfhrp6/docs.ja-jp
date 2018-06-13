---
title: 構造体のデザイン
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2621aa96cf89b453d5faec3357d0890ca36251d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572737"
---
# <a name="struct-design"></a><span data-ttu-id="084d0-102">構造体のデザイン</span><span class="sxs-lookup"><span data-stu-id="084d0-102">Struct Design</span></span>
<span data-ttu-id="084d0-103">ほとんどの場合に、汎用的な値の型を構造体、その c# キーワードと呼びます。</span><span class="sxs-lookup"><span data-stu-id="084d0-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="084d0-104">このセクションでは、一般的な構造体のデザインのガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="084d0-104">This section provides guidelines for general struct design.</span></span>  
  
 <span data-ttu-id="084d0-105">**X しないで**構造体の既定のコンス トラクターを提供します。</span><span class="sxs-lookup"><span data-stu-id="084d0-105">**X DO NOT** provide a default constructor for a struct.</span></span>  
  
 <span data-ttu-id="084d0-106">このガイドラインに従う、配列の各項目で、コンス トラクターを実行しなくても作成する構造体の配列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="084d0-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="084d0-107">C# は許可されていないことを既定のコンス トラクターを持つ構造体に注意してください。</span><span class="sxs-lookup"><span data-stu-id="084d0-107">Notice that C# does not allow structs to have default constructors.</span></span>  
  
 <span data-ttu-id="084d0-108">**X しないで**変更可能な値の型を定義します。</span><span class="sxs-lookup"><span data-stu-id="084d0-108">**X DO NOT** define mutable value types.</span></span>  
  
 <span data-ttu-id="084d0-109">変更可能な値の型には、いくつかの問題があります。</span><span class="sxs-lookup"><span data-stu-id="084d0-109">Mutable value types have several problems.</span></span> <span data-ttu-id="084d0-110">たとえば、プロパティ get アクセス操作子が値型を返すときに、呼び出し元は、コピーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="084d0-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="084d0-111">コピーが暗黙的に作成されるため、開発者が、コピー、および元の値ではなくを変更することに注意してくださいできない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="084d0-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="084d0-112">また、一部の言語 (動的言語、特に) では、逆参照時に、ローカル変数があっても、コピーできるようにするために、変更可能な値の型を使用して問題があります。</span><span class="sxs-lookup"><span data-stu-id="084d0-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>  
  
 <span data-ttu-id="084d0-113">**✓ しないで**すべてのインスタンス データの状態が 0 に設定されている、false の場合、または null (該当する場合) が有効であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="084d0-113">**✓ DO** ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>  
  
 <span data-ttu-id="084d0-114">構造体の配列の作成時に、無効なインスタンスの偶発的な作成ができなくなります。</span><span class="sxs-lookup"><span data-stu-id="084d0-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>  
  
 <span data-ttu-id="084d0-115">**✓ は**実装<xref:System.IEquatable%601>を値の型。</span><span class="sxs-lookup"><span data-stu-id="084d0-115">**✓ DO** implement <xref:System.IEquatable%601> on value types.</span></span>  
  
 <span data-ttu-id="084d0-116"><xref:System.Object.Equals%2A?displayProperty=nameWithType>メソッド値の型をボックス化、発生して、既定の実装はリフレクションを使用しているため、非常に効率はします。</span><span class="sxs-lookup"><span data-stu-id="084d0-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="084d0-117"><xref:System.IEquatable%601.Equals%2A> 多くのパフォーマンスが向上し、ボックス化は発生しませんできるように実装することができます。</span><span class="sxs-lookup"><span data-stu-id="084d0-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>  
  
 <span data-ttu-id="084d0-118">**X しないで**明示的に拡張<xref:System.ValueType>です。</span><span class="sxs-lookup"><span data-stu-id="084d0-118">**X DO NOT** explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="084d0-119">実際には、ほとんどの言語は、これを防ぐ。</span><span class="sxs-lookup"><span data-stu-id="084d0-119">In fact, most languages prevent this.</span></span>  
  
 <span data-ttu-id="084d0-120">一般に、構造体は、非常に役に立ちますが、いないボックス化頻繁に小さく、1 つ、変更できない値に対してのみ使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="084d0-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>  
  
 <span data-ttu-id="084d0-121">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="084d0-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="084d0-122">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="084d0-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="084d0-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="084d0-123">See Also</span></span>  
 [<span data-ttu-id="084d0-124">型デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="084d0-124">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="084d0-125">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="084d0-125">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="084d0-126">クラスまたは構造体の選択</span><span class="sxs-lookup"><span data-stu-id="084d0-126">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
