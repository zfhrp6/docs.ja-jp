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
# <a name="performing-culture-insensitive-string-operations-in-collections"></a>カルチャを認識しないコレクションの操作の実行
クラスとメンバーがある、<xref:System.Collections>名前空間を既定ではカルチャに依存した動作を提供します。 既定のコンス トラクター、<xref:System.Collections.CaseInsensitiveComparer>と<xref:System.Collections.CaseInsensitiveHashCodeProvider>クラスの新しいインスタンスを使用して、初期化、<xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType>プロパティです。 すべてのオーバー ロード、<xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>メソッドの新しいインスタンスを作成する、<xref:System.Collections.Hashtable>クラスを使用して、`Thread.CurrentCulture`既定ではプロパティです。 オーバー ロードが、<xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>メソッドは、既定値を使用してカルチャに依存した並べ替えを実行`Thread.CurrentCulture`です。 並べ替えと検索、<xref:System.Collections.SortedList>影響を受ける`Thread.CurrentCulture`キーとして文字列を使用する場合。 このセクションで説明する推奨使用方法に従うと、`Collections` 名前空間のこれらのクラスとメソッドでカルチャを認識しない結果が得られます。  
  
 **注**渡す<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>を比較するメソッドは、カルチャに依存しない比較を実行します。 ただし、これによって、ファイル パス、レジストリ キー、環境変数などで、非言語的な比較が行われることはありません。 また、比較結果に基づいたセキュリティに関する決定もサポートされません。 非言語的な比較または結果ベースのセキュリティを決定するためのサポートは、アプリケーション メソッドを使用して、比較を受け付ける、<xref:System.StringComparison>値。 アプリケーションに渡す必要があります、<xref:System.StringComparison>です。  
  
## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a>CaseInsensitiveComparer クラスおよび CaseInsensitiveHashCodeProvider クラスの使用  
 `CaseInsensitiveHashCodeProvider` および `CaseInsensitiveComparer` の既定コンストラクターは、`Thread.CurrentCulture` を使用してクラスの新しいインスタンスを初期化し、その結果としてカルチャを認識した動作が行われます。 次のコード例は `Hashtable` を示します。これがカルチャを認識するのは、`CaseInsensitiveHashCodeProvider` と `CaseInsensitiveComparer` の既定コンストラクターを使用するためです。  
  
```vb  
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)  
```  
  
```csharp  
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);  
```  
  
 カルチャに依存しないを作成する場合`Hashtable`を使用して、`CaseInsensitiveComparer`と`CaseInsensitiveHashCodeProvider`クラスを受け入れるコンス トラクターを使用してこれらのクラスの新しいインスタンスを初期化、`culture`パラメーター。 `culture` パラメーターに <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> を指定してください。 カルチャを認識しない `Hashtable` を次のコード例で示します。  
  
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
  
## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a>CollectionsUtil.CreateCaseInsensitiveHashTable メソッドの使用  
 `CollectionsUtil.CreateCaseInsensitiveHashTable` メソッドは、文字列の大文字と小文字を無視する `Hashtable` クラスの新しいインスタンスを手早く作成する便利な方法です。 ただし、`CollectionsUtil.CreateCaseInsensitiveHashTable` メソッドのすべてのオーバーロードは、`Thread.CurrentCulture` プロパティを使用するためカルチャを認識します。 このメソッドを使用して、カルチャを認識しない `Hashtable` を作成することはできません。 カルチャを認識しない `Hashtable` を作成するには、`culture`パラメーターを受け取る `Hashtable` コンストラクターを使用します。 `culture` パラメーターに `CultureInfo.InvariantCulture` を指定してください。 カルチャを認識しない `Hashtable` を次のコード例で示します。  
  
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
## <a name="using-the-sortedlist-class"></a>SortedList クラスの使用  
 `SortedList`は、キーによって並べ替えられ、キーとインデックスを使ってアクセスできる、キーと値のペアのコレクションを表します。 文字列がキーであるときに `SortedList` を使用すると、並べ替えと検索が `Thread.CurrentCulture` プロパティの影響を受けることがあります。 `SortedList` でカルチャを認識しない動作を実行するには、`comparer` パラメーターを受け取るコンストラクターの 1 つを使用して `SortedList` を作成します。 `comparer`パラメーターを指定します、<xref:System.Collections.IComparer>キーを比較するときに使用する実装。 このパラメーターには、キーを比較するために `CultureInfo.InvariantCulture` を使用するカスタム comparer クラスを指定してください。 次の例は、カルチャを認識しないカスタム comparer クラスです。これは `SortedList`コンストラクターの `comparer` パラメーターとして指定できます。  
  
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
  
 一般に、`SortedList` を文字列に対して使用する際にカスタム invariant comparer を指定しないと、リストにデータが設定された後で、`Thread.CurrentCulture` に対する変更によってリストが無効になることがあります。  
  
## <a name="using-the-arraylistsort-method"></a>ArrayList.Sort メソッドの使用  
 `ArrayList.Sort` メソッドのオーバーロードは、`Thread.CurrentCulture`プロパティを使用して、カルチャを認識する並べ替えを既定で実行します。 結果は、さまざまな並べ替え順序のためカルチャによって変わることがあります。 カルチャを認識した動作を回避するには、`IComparer`実装を受け入れるこのメソッドのオーバーロードを使用します。 `comparer` パラメーターには、`CultureInfo.InvariantCulture` を使用するカスタム invariant comparer クラスを指定してください。 カスタム invariant comparer クラスの例は、「[SortedList クラスの使用](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1)」のトピックをご覧ください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Collections.CaseInsensitiveComparer>  
 <xref:System.Collections.CaseInsensitiveHashCodeProvider>  
 <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Collections.SortedList>  
 <xref:System.Collections.Hashtable>  
 <xref:System.Collections.IComparer>  
 [カルチャを認識しない文字列操作の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
 <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
