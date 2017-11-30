---
title: "カルチャを認識しないコレクションの操作の実行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CaseInsensitiveComparer class, using
- CollectionsUtil.CreateCaseInsensitiveHashtable method
- culture-insensitive string operations, collections
- collections [.NET Framework], culture-insensitive string operations
- CaseInsensitiveHashCodeProvider class, using
- ArrayList.Sort method
- SortedList class, culture-insensitive string operations
- culture parameter
ms.assetid: 5cdc9396-a64b-4615-a1cd-b605db4c5983
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a1ecba9c055f8e99d26283c7f37c2430dc17bf31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a><span data-ttu-id="d90f4-102">カルチャを認識しないコレクションの操作の実行</span><span class="sxs-lookup"><span data-stu-id="d90f4-102">Performing Culture-Insensitive String Operations in Collections</span></span>
<span data-ttu-id="d90f4-103">クラスとメンバーがある、<xref:System.Collections>名前空間を既定ではカルチャに依存した動作を提供します。</span><span class="sxs-lookup"><span data-stu-id="d90f4-103">There are classes and members in the <xref:System.Collections> namespace that provide culture-sensitive behavior by default.</span></span> <span data-ttu-id="d90f4-104">既定のコンス トラクター、<xref:System.Collections.CaseInsensitiveComparer>と<xref:System.Collections.CaseInsensitiveHashCodeProvider>クラスの新しいインスタンスを使用して、初期化、<xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d90f4-104">The default constructors for the <xref:System.Collections.CaseInsensitiveComparer> and <xref:System.Collections.CaseInsensitiveHashCodeProvider> classes initialize a new instance using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="d90f4-105">すべてのオーバー ロード、<xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>メソッドの新しいインスタンスを作成する、<xref:System.Collections.Hashtable>クラスを使用して、`Thread.CurrentCulture`既定ではプロパティです。</span><span class="sxs-lookup"><span data-stu-id="d90f4-105">All overloads of the <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> method create a new instance of the <xref:System.Collections.Hashtable> class using the `Thread.CurrentCulture` property by default.</span></span> <span data-ttu-id="d90f4-106">オーバー ロードが、<xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>メソッドは、既定値を使用してカルチャに依存した並べ替えを実行`Thread.CurrentCulture`です。</span><span class="sxs-lookup"><span data-stu-id="d90f4-106">Overloads of the <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> method perform culture-sensitive sorts by default using `Thread.CurrentCulture`.</span></span> <span data-ttu-id="d90f4-107">並べ替えと検索、<xref:System.Collections.SortedList>影響を受ける`Thread.CurrentCulture`キーとして文字列を使用する場合。</span><span class="sxs-lookup"><span data-stu-id="d90f4-107">Sorting and lookup in a <xref:System.Collections.SortedList> can be affected by `Thread.CurrentCulture` when strings are used as the keys.</span></span> <span data-ttu-id="d90f4-108">このセクションで説明する推奨使用方法に従うと、`Collections` 名前空間のこれらのクラスとメソッドでカルチャを認識しない結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="d90f4-108">Follow the usage recommendations provided in this section to obtain culture-insensitive results from these classes and methods in the `Collections` namespace.</span></span>  
  
 <span data-ttu-id="d90f4-109">**注**渡す<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>を比較するメソッドは、カルチャに依存しない比較を実行します。</span><span class="sxs-lookup"><span data-stu-id="d90f4-109">**Note** Passing <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="d90f4-110">ただし、これによって、ファイル パス、レジストリ キー、環境変数などで、非言語的な比較が行われることはありません。</span><span class="sxs-lookup"><span data-stu-id="d90f4-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="d90f4-111">また、比較結果に基づいたセキュリティに関する決定もサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d90f4-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="d90f4-112">非言語的な比較または結果ベースのセキュリティを決定するためのサポートは、アプリケーション メソッドを使用して、比較を受け付ける、<xref:System.StringComparison>値。</span><span class="sxs-lookup"><span data-stu-id="d90f4-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="d90f4-113">アプリケーションに渡す必要があります、<xref:System.StringComparison>です。</span><span class="sxs-lookup"><span data-stu-id="d90f4-113">The application should then pass <xref:System.StringComparison>.</span></span>  
  
## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a><span data-ttu-id="d90f4-114">CaseInsensitiveComparer クラスおよび CaseInsensitiveHashCodeProvider クラスの使用</span><span class="sxs-lookup"><span data-stu-id="d90f4-114">Using the CaseInsensitiveComparer and CaseInsensitiveHashCodeProvider Classes</span></span>  
 <span data-ttu-id="d90f4-115">`CaseInsensitiveHashCodeProvider` および `CaseInsensitiveComparer` の既定コンストラクターは、`Thread.CurrentCulture` を使用してクラスの新しいインスタンスを初期化し、その結果としてカルチャを認識した動作が行われます。</span><span class="sxs-lookup"><span data-stu-id="d90f4-115">The default constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer` initialize a new instance of the class using the `Thread.CurrentCulture`, resulting in culture-sensitive behavior.</span></span> <span data-ttu-id="d90f4-116">次のコード例は `Hashtable` を示します。これがカルチャを認識するのは、`CaseInsensitiveHashCodeProvider` と `CaseInsensitiveComparer` の既定コンストラクターを使用するためです。</span><span class="sxs-lookup"><span data-stu-id="d90f4-116">The following code example demonstrates the constructor for a `Hashtable` that is culture-sensitive because it uses the default constructors for `CaseInsensitiveHashCodeProvider` and `CaseInsensitiveComparer`.</span></span>  
  
```vb  
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)  
```  
  
```csharp  
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);  
```  
  
 <span data-ttu-id="d90f4-117">カルチャに依存しないを作成する場合`Hashtable`を使用して、`CaseInsensitiveComparer`と`CaseInsensitiveHashCodeProvider`クラスを受け入れるコンス トラクターを使用してこれらのクラスの新しいインスタンスを初期化、`culture`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="d90f4-117">If you want to create a culture-insensitive `Hashtable` using the `CaseInsensitiveComparer` and `CaseInsensitiveHashCodeProvider` classes, initialize new instances of these classes using the constructors that accept a `culture` parameter.</span></span> <span data-ttu-id="d90f4-118">`culture` パラメーターに <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> を指定してください。</span><span class="sxs-lookup"><span data-stu-id="d90f4-118">For the `culture` parameter, specify <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d90f4-119">カルチャを認識しない `Hashtable` を次のコード例で示します。</span><span class="sxs-lookup"><span data-stu-id="d90f4-119">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>  
  
```vb  
internalHashtable = New Hashtable(New  
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),  
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))  
```  
  
```csharp  
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider  
    (CultureInfo.InvariantCulture),   
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));  
```  
  
## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a><span data-ttu-id="d90f4-120">CollectionsUtil.CreateCaseInsensitiveHashTable メソッドの使用</span><span class="sxs-lookup"><span data-stu-id="d90f4-120">Using the CollectionsUtil.CreateCaseInsensitiveHashTable Method</span></span>  
 <span data-ttu-id="d90f4-121">`CollectionsUtil.CreateCaseInsensitiveHashTable` メソッドは、文字列の大文字と小文字を無視する `Hashtable` クラスの新しいインスタンスを手早く作成する便利な方法です。</span><span class="sxs-lookup"><span data-stu-id="d90f4-121">The `CollectionsUtil.CreateCaseInsensitiveHashTable` method is a useful shortcut for creating a new instance of the `Hashtable` class that ignores the case of strings.</span></span> <span data-ttu-id="d90f4-122">ただし、`CollectionsUtil.CreateCaseInsensitiveHashTable` メソッドのすべてのオーバーロードは、`Thread.CurrentCulture` プロパティを使用するためカルチャを認識します。</span><span class="sxs-lookup"><span data-stu-id="d90f4-122">However, all overloads of the `CollectionsUtil.CreateCaseInsensitiveHashTable` method are culture-sensitive because they use the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="d90f4-123">このメソッドを使用して、カルチャを認識しない `Hashtable` を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="d90f4-123">You cannot create a culture-insensitive `Hashtable` using this method.</span></span> <span data-ttu-id="d90f4-124">カルチャを認識しない `Hashtable` を作成するには、`culture`パラメーターを受け取る `Hashtable` コンストラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="d90f4-124">To create a culture-insensitive `Hashtable`, use the `Hashtable` constructor that accepts a `culture` parameter.</span></span> <span data-ttu-id="d90f4-125">`culture` パラメーターに `CultureInfo.InvariantCulture` を指定してください。</span><span class="sxs-lookup"><span data-stu-id="d90f4-125">For the `culture` parameter, specify `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="d90f4-126">カルチャを認識しない `Hashtable` を次のコード例で示します。</span><span class="sxs-lookup"><span data-stu-id="d90f4-126">The following code example demonstrates the constructor for a culture-insensitive `Hashtable`.</span></span>  
  
```vb  
internalHashtable = New Hashtable(New  
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),  
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))  
```  
  
```csharp  
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider  
    (CultureInfo.InvariantCulture),   
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));  
```  
  
<a name="cpconperformingculture-insensitivestringoperationsincollectionsanchor1"></a>   
## <a name="using-the-sortedlist-class"></a><span data-ttu-id="d90f4-127">SortedList クラスの使用</span><span class="sxs-lookup"><span data-stu-id="d90f4-127">Using the SortedList Class</span></span>  
 <span data-ttu-id="d90f4-128">`SortedList`は、キーによって並べ替えられ、キーとインデックスを使ってアクセスできる、キーと値のペアのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="d90f4-128">A `SortedList` represents a collection of key-and-value pairs that are sorted by the keys and are accessible by key and by index.</span></span> <span data-ttu-id="d90f4-129">文字列がキーであるときに `SortedList` を使用すると、並べ替えと検索が `Thread.CurrentCulture` プロパティの影響を受けることがあります。</span><span class="sxs-lookup"><span data-stu-id="d90f4-129">When you use a `SortedList` where strings are the keys, the sorting and lookup can be affected by the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="d90f4-130">`SortedList` でカルチャを認識しない動作を実行するには、`comparer` パラメーターを受け取るコンストラクターの 1 つを使用して `SortedList` を作成します。</span><span class="sxs-lookup"><span data-stu-id="d90f4-130">To obtain culture-insensitive behavior from a `SortedList`, create a `SortedList` using one of the constructors that accepts a `comparer` parameter.</span></span> <span data-ttu-id="d90f4-131">`comparer`パラメーターを指定します、<xref:System.Collections.IComparer>キーを比較するときに使用する実装。</span><span class="sxs-lookup"><span data-stu-id="d90f4-131">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing keys.</span></span> <span data-ttu-id="d90f4-132">このパラメーターには、キーを比較するために `CultureInfo.InvariantCulture` を使用するカスタム comparer クラスを指定してください。</span><span class="sxs-lookup"><span data-stu-id="d90f4-132">For the parameter, specify a custom comparer class that uses `CultureInfo.InvariantCulture` to compare keys.</span></span> <span data-ttu-id="d90f4-133">次の例は、カルチャを認識しないカスタム comparer クラスです。これは `SortedList`コンストラクターの `comparer` パラメーターとして指定できます。</span><span class="sxs-lookup"><span data-stu-id="d90f4-133">The following example illustrates a custom culture-insensitive comparer class that you can specify as the `comparer` parameter to a `SortedList` constructor.</span></span>  
  
```vb  
Imports System  
Imports System.Collections  
Imports System.Globalization  
  
Friend Class InvariantComparer  
    Implements IComparer   
    Private m_compareInfo As CompareInfo  
    Friend Shared [Default] As New InvariantComparer()  
  
    Friend Sub New()  
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo  
    End Sub     
  
    Public Function Compare(a As Object, b As Object) As Integer _  
            Implements IComparer.Compare  
        Dim sa As String = CType(a, String)  
        Dim sb As String = CType(b, String)  
        If Not (sa Is Nothing) And Not (sb Is Nothing) Then  
            Return m_compareInfo.Compare(sa, sb)  
        Else  
            Return Comparer.Default.Compare(a, b)  
        End If  
    End Function  
End Class  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Globalization;  
  
internal class InvariantComparer : IComparer   
{  
    private CompareInfo m_compareInfo;  
    internal static readonly InvariantComparer Default = new  
        InvariantComparer();  
  
    internal InvariantComparer()   
    {  
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo;  
    }  
  
    public int Compare(Object a, Object b)  
    {  
        String sa = a as String;  
        String sb = b as String;  
        if (sa != null && sb != null)  
            return m_compareInfo.Compare(sa, sb);  
        else  
            return Comparer.Default.Compare(a,b);  
    }  
}  
```  
  
 <span data-ttu-id="d90f4-134">一般に、`SortedList` を文字列に対して使用する際にカスタム invariant comparer を指定しないと、リストにデータが設定された後で、`Thread.CurrentCulture` に対する変更によってリストが無効になることがあります。</span><span class="sxs-lookup"><span data-stu-id="d90f4-134">In general, if you use a `SortedList` on strings without specifying a custom invariant comparer, a change to `Thread.CurrentCulture` after the list has been populated can invalidate the list.</span></span>  
  
## <a name="using-the-arraylistsort-method"></a><span data-ttu-id="d90f4-135">ArrayList.Sort メソッドの使用</span><span class="sxs-lookup"><span data-stu-id="d90f4-135">Using the ArrayList.Sort Method</span></span>  
 <span data-ttu-id="d90f4-136">`ArrayList.Sort` メソッドのオーバーロードは、`Thread.CurrentCulture`プロパティを使用して、カルチャを認識する並べ替えを既定で実行します。</span><span class="sxs-lookup"><span data-stu-id="d90f4-136">Overloads of the `ArrayList.Sort` method perform culture-sensitive sorts by default using the `Thread.CurrentCulture` property.</span></span> <span data-ttu-id="d90f4-137">結果は、さまざまな並べ替え順序のためカルチャによって変わることがあります。</span><span class="sxs-lookup"><span data-stu-id="d90f4-137">Results can vary by culture due to different sort orders.</span></span> <span data-ttu-id="d90f4-138">カルチャを認識した動作を回避するには、`IComparer`実装を受け入れるこのメソッドのオーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="d90f4-138">To eliminate culture-sensitive behavior, use the overloads of this method that accept an `IComparer` implementation.</span></span> <span data-ttu-id="d90f4-139">`comparer` パラメーターには、`CultureInfo.InvariantCulture` を使用するカスタム invariant comparer クラスを指定してください。</span><span class="sxs-lookup"><span data-stu-id="d90f4-139">For the `comparer` parameter, specify a custom invariant comparer class that uses `CultureInfo.InvariantCulture`.</span></span> <span data-ttu-id="d90f4-140">カスタム invariant comparer クラスの例は、「[SortedList クラスの使用](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1)」のトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d90f4-140">An example of a custom invariant comparer class is provided in the [Using the SortedList Class](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d90f4-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="d90f4-141">See Also</span></span>  
 <xref:System.Collections.CaseInsensitiveComparer>  
 <xref:System.Collections.CaseInsensitiveHashCodeProvider>  
 <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Collections.SortedList>  
 <xref:System.Collections.Hashtable>  
 <xref:System.Collections.IComparer>  
 [<span data-ttu-id="d90f4-142">カルチャを認識しない文字列操作の実行</span><span class="sxs-lookup"><span data-stu-id="d90f4-142">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
 <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
