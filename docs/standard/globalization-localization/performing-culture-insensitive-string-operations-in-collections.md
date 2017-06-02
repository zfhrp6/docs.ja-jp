---
title: "カルチャを認識しないコレクションの操作の実行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ArrayList.Sort メソッド"
  - "CaseInsensitiveComparer クラス, 使用"
  - "CaseInsensitiveHashCodeProvider クラス, 使用"
  - "コレクション [.NET Framework], カルチャを認識しない文字列操作"
  - "CollectionsUtil.CreateCaseInsensitiveHashtable メソッド"
  - "culture パラメーター"
  - "カルチャを認識しない文字列操作, コレクション"
  - "SortedList クラス, カルチャを認識しない文字列操作"
ms.assetid: 5cdc9396-a64b-4615-a1cd-b605db4c5983
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# カルチャを認識しないコレクションの操作の実行
<xref:System.Collections> 名前空間には、既定の動作でカルチャに依存するクラスとメンバーがあります。  <xref:System.Collections.CaseInsensitiveComparer> クラスと <xref:System.Collections.CaseInsensitiveHashCodeProvider> クラスの既定のコンストラクターは、<xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=fullName> プロパティを使用して新しいインスタンスを初期化します。  [CollectionsUtil.CreateCaseInsensitiveHashTable](frlrfSystemCollectionsSpecializedCollectionsUtilClassCreateCaseInsensitiveHashtableTopic) メソッドのすべてのオーバーロードは、既定で `Thread.CurrentCulture` プロパティを使用して <xref:System.Collections.Hashtable> クラスの新しいインスタンスを作成します。  <xref:System.Collections.ArrayList.Sort%2A?displayProperty=fullName> メソッドのオーバーロードは、既定で `Thread.CurrentCulture` を使用してカルチャに依存した並べ替えを実行します。  文字列をキーとして使用する場合、<xref:System.Collections.SortedList> の並べ替えと検索は `Thread.CurrentCulture` の影響を受けることがあります。  `Collections` 名前空間のこれらのクラスおよびメソッドからカルチャに依存しない結果を取得するには、後で説明する使用に関する推奨事項に従ってください。  
  
 **メモ** 比較メソッドに <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> を渡すと、カルチャに依存しない比較が実行されます。  ただし、この場合、ファイル パス、レジストリ キー、環境変数などに関する非言語的な比較は行われません。  また、比較結果に基づくセキュリティの決定もサポートされません。  非言語的な比較を行う場合、または結果に基づくセキュリティの決定をサポートする場合は、<xref:System.StringComparison> 値を受け取る比較メソッドを使用し、  <xref:System.StringComparison> を渡す必要があります。  
  
## CaseInsensitiveComparer クラスと CaseInsensitiveHashCodeProvider クラスの使用  
 `CaseInsensitiveHashCodeProvider` と `CaseInsensitiveComparer` の既定のコンストラクターは、`Thread.CurrentCulture` を使用してクラスの新しいインスタンスを初期化するため、その動作はカルチャに依存します。  次のコード例に示す `Hashtable` のコンストラクターは、`CaseInsensitiveHashCodeProvider` と `CaseInsensitiveComparer` の既定のコンストラクターを使用しているため、カルチャに依存します。  
  
```vb  
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)  
  
```  
  
```csharp  
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);  
```  
  
 `CaseInsensitiveComparer` クラスと `CaseInsensitiveHashCodeProvider` クラスを使用してカルチャに依存しない `Hashtable` を作成するには、`culture` パラメーターを受け取るコンストラクターを使用してこれらのクラスの新しいインスタンスを初期化します。  `culture` パラメーターには、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> を指定します。  カルチャに依存しない `Hashtable` のコンストラクターを次のコード例に示します。  
  
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
  
## CollectionsUtil.CreateCaseInsensitiveHashTable メソッドの使用  
 `CollectionsUtil.CreateCaseInsensitiveHashTable` メソッドは、文字列の大文字と小文字の区別を無視する `Hashtable` クラスの新しいインスタンスを作成するための便利なショートカットです。  ただし、`CollectionsUtil.CreateCaseInsensitiveHashTable` メソッドのオーバーロードはすべて `Thread.CurrentCulture` プロパティを使用するため、カルチャに依存します。  このメソッドを使用して、カルチャに依存しない `Hashtable` を作成することはできません。  カルチャに依存しない `Hashtable` を作成するには、`culture` パラメーターを受け取る `Hashtable` のコンストラクターを使用します。  `culture` パラメーターには、`CultureInfo.InvariantCulture` を指定します。  カルチャに依存しない `Hashtable` のコンストラクターを次のコード例に示します。  
  
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
## SortedList クラスの使用  
 `SortedList` は、キーで並べ替えられ、キーやインデックスでアクセスできるキーと値の組み合わせのコレクションを表します。  文字列がキーである `SortedList` を使用すると、並べ替えおよび検索が `Thread.CurrentCulture` プロパティの影響を受ける可能性があります。  `SortedList` の動作がカルチャに依存しないようにするには、`comparer` パラメーターを受け取るコンストラクターを使用して `SortedList` を作成します。  `comparer` パラメーターは、キーを比較するときに使用する <xref:System.Collections.IComparer> の実装を指定します。  このパラメーターには、`CultureInfo.InvariantCulture` を使用してキーを比較するカスタム比較子クラスを指定します。  `SortedList` コンストラクターの `comparer` パラメーターとして指定できる、カルチャに依存しないカスタム比較子クラスの例を次に示します。  
  
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
  
 一般的に、カスタム インバリアント比較子を指定せずに、文字列に対して `SortedList` を使用した場合は、リストが作成された後に `Thread.CurrentCulture` を変更するとリストが無効になることがあります。  
  
## ArrayList.Sort メソッドの使用  
 `ArrayList.Sort` メソッドのオーバーロードは、既定で `Thread.CurrentCulture` プロパティを使用してカルチャに依存した並べ替えを実行します。  結果は、並べ替えの順序が異なるため、カルチャごとに異なることがあります。  動作がカルチャに依存しないようにするには、`IComparer` 実装を受け取るこのメソッドのオーバーロードを使用します。  `comparer` パラメーターには、`CultureInfo.InvariantCulture` を使用するカスタム インバリアント比較子クラスを指定します。  カスタム インバリアント比較子クラスの例については、「[SortedList クラスの使用](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1)」を参照してください。  
  
## 参照  
 <xref:System.Collections.CaseInsensitiveComparer>   
 <xref:System.Collections.CaseInsensitiveHashCodeProvider>   
 <xref:System.Collections.ArrayList.Sort%2A?displayProperty=fullName>   
 <xref:System.Collections.SortedList>   
 <xref:System.Collections.Hashtable>   
 <xref:System.Collections.IComparer>   
 [カルチャを認識しない文字列操作の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)   
 [CollectionsUtil.CreateCaseInsensitiveHashTable メソッド](frlrfSystemCollectionsSpecializedCollectionsUtilClassCreateCaseInsensitiveHashtableTopic)