---
title: ".NET Framework クラス ライブラリのジェネリック (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], in .NET Framework class library
ms.assetid: afdd5477-6770-4686-8297-f58a4d749daf
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f3d5f15c92031301b68c6a702cf8d6b135cca36d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="generics-in-the-net-framework-class-library-c-programming-guide"></a><span data-ttu-id="251b4-102">.NET Framework クラス ライブラリのジェネリック (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="251b4-102">Generics in the .NET Framework Class Library (C# Programming Guide)</span></span>
<span data-ttu-id="251b4-103">.NET Framework Version 2.0 のクラス ライブラリで提供される新しい名前空間 <xref:System.Collections.Generic> には、すぐに利用できるジェネリック コレクション クラスや関連するインターフェイスがいくつか含まれています。</span><span class="sxs-lookup"><span data-stu-id="251b4-103">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which includes several ready-to-use generic collection classes and associated interfaces.</span></span> <span data-ttu-id="251b4-104">その他の名前空間 (<xref:System> など) にも、新しいジェネリック インターフェイス (<xref:System.IComparable%601> など) が用意されています。</span><span class="sxs-lookup"><span data-stu-id="251b4-104">Other namespaces, such as <xref:System>, also provide new generic interfaces such as <xref:System.IComparable%601>.</span></span> <span data-ttu-id="251b4-105">これらのクラスとインターフェイスは、.NET Framework の以前のバージョンに用意されていた非ジェネリック コレクション クラスよりも効率的かつタイプ セーフです。</span><span class="sxs-lookup"><span data-stu-id="251b4-105">These classes and interfaces are more efficient and type-safe than the non-generic collection classes provided in earlier releases of the .NET Framework.</span></span> <span data-ttu-id="251b4-106">カスタム コレクション クラスを独自に設計して実装する前に、.NET Framework のクラス ライブラリに用意されているいずれかのクラスを使用できないか、それらのクラスからクラスを派生できないかを検討してください。</span><span class="sxs-lookup"><span data-stu-id="251b4-106">Before designing and implementing your own custom collection classes, consider whether you can use or derive a class from one of the classes provided in the .NET Framework class library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="251b4-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="251b4-107">See Also</span></span>  
 <span data-ttu-id="251b4-108">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="251b4-108">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="251b4-109">[ジェネリック コレクションを使用する状況](../../../standard/collections/when-to-use-generic-collections.md) </span><span class="sxs-lookup"><span data-stu-id="251b4-109">[When to Use Generic Collections](../../../standard/collections/when-to-use-generic-collections.md) </span></span>  
 <span data-ttu-id="251b4-110">[コレクションとデータ構造体](../../../standard/collections/index.md) </span><span class="sxs-lookup"><span data-stu-id="251b4-110">[Collections and Data Structures](../../../standard/collections/index.md) </span></span>  
 [<span data-ttu-id="251b4-111">ジェネリックの概要</span><span class="sxs-lookup"><span data-stu-id="251b4-111">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)

