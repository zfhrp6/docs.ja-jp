---
title: ".NET Framework クラス ライブラリのジェネリック (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], in .NET Framework class library
ms.assetid: afdd5477-6770-4686-8297-f58a4d749daf
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 83ce8b8fe31a35e04c23c316ead5848aec79ec42
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="generics-in-the-net-framework-class-library-c-programming-guide"></a><span data-ttu-id="94a8a-102">.NET Framework クラス ライブラリのジェネリック (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="94a8a-102">Generics in the .NET Framework Class Library (C# Programming Guide)</span></span>
<span data-ttu-id="94a8a-103">.NET Framework Version 2.0 のクラス ライブラリで提供される新しい名前空間 <xref:System.Collections.Generic> には、すぐに利用できるジェネリック コレクション クラスや関連するインターフェイスがいくつか含まれています。</span><span class="sxs-lookup"><span data-stu-id="94a8a-103">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which includes several ready-to-use generic collection classes and associated interfaces.</span></span> <span data-ttu-id="94a8a-104">その他の名前空間 (<xref:System> など) にも、新しいジェネリック インターフェイス (<xref:System.IComparable%601> など) が用意されています。</span><span class="sxs-lookup"><span data-stu-id="94a8a-104">Other namespaces, such as <xref:System>, also provide new generic interfaces such as <xref:System.IComparable%601>.</span></span> <span data-ttu-id="94a8a-105">これらのクラスとインターフェイスは、.NET Framework の以前のバージョンに用意されていた非ジェネリック コレクション クラスよりも効率的かつタイプ セーフです。</span><span class="sxs-lookup"><span data-stu-id="94a8a-105">These classes and interfaces are more efficient and type-safe than the non-generic collection classes provided in earlier releases of the .NET Framework.</span></span> <span data-ttu-id="94a8a-106">カスタム コレクション クラスを独自に設計して実装する前に、.NET Framework のクラス ライブラリに用意されているいずれかのクラスを使用できないか、それらのクラスからクラスを派生できないかを検討してください。</span><span class="sxs-lookup"><span data-stu-id="94a8a-106">Before designing and implementing your own custom collection classes, consider whether you can use or derive a class from one of the classes provided in the .NET Framework class library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94a8a-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="94a8a-107">See Also</span></span>  
 [<span data-ttu-id="94a8a-108">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="94a8a-108">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="94a8a-109">ジェネリック コレクションを使用する状況</span><span class="sxs-lookup"><span data-stu-id="94a8a-109">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)  
 [<span data-ttu-id="94a8a-110">コレクションとデータ構造体</span><span class="sxs-lookup"><span data-stu-id="94a8a-110">Collections and Data Structures</span></span>](../../../standard/collections/index.md)  
 [<span data-ttu-id="94a8a-111">ジェネリックの概要</span><span class="sxs-lookup"><span data-stu-id="94a8a-111">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)
