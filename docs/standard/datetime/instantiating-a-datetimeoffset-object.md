---
title: "DateTimeOffset オブジェクトのインスタンス化 | Microsoft Docs"
ms.custom: ""
ms.date: "04/10/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "インスタンス化 (タイム ゾーン オブジェクトを)"
  - "タイム ゾーン オブジェクト [.NET Framework]、インスタンス化"
  - "DateTimeOffset 構造体、変換 (DateTime に)"
  - "DateTimeOffset 構造体、インスタンス化"
ms.assetid: 9648375f-d368-4373-a976-3332ece00c0a
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# DateTimeOffset オブジェクトのインスタンス化
<xref:System.DateTimeOffset> 構造体は <xref:System.DateTimeOffset> 新しい値を作成する方法を示します。  大部分の方法は、新しい <xref:System.DateTime> 値のインスタンス化に利用できるメソッドに直接対応しています。このメソッドには拡張が施されており、世界協定時刻 \(UTC: Coordinated Universal Time\) からの日付と時刻の値のオフセットを指定できます。  具体的には、次の方法を使用して <xref:System.DateTimeOffset> 値をインスタンス化できます。  
  
-   日付リテラルと時刻リテラルを使用する。  
  
-   <xref:System.DateTimeOffset> コンストラクターを呼び出す。  
  
-   値を <xref:System.DateTimeOffset> 値に暗黙に変換する。  
  
-   日付と時刻の文字列形式を解析する。  
  
 このトピックでは、これらの方法を使用して新しい <xref:System.DateTimeOffset> 値をインスタンス化する方法を詳述し、コード例を示します。  
  
## 日付リテラルと時刻リテラル  
 <xref:System.DateTime> 値をインスタンス化する最も一般的な方法は、日付と時刻を、ハードコーディングされたリテラル値としてインスタンス化することです \(言語がサポートしている場合\)。  たとえば、次の Visual Basic コードは、値が 2008 年 1 月 1 日午前 10 時を示す <xref:System.DateTime> オブジェクトを作成します。  
  
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]  
  
 <xref:System.DateTime> リテラルをサポートする言語を使用する場合は、日付リテラルと時刻リテラルを使用して <xref:System.DateTimeOffset> 値を初期化することもできます。  たとえば、次の Visual Basic コードは、<xref:System.DateTimeOffset> オブジェクトを作成します。  
  
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]  
  
 ファイルの出力を見てわかるように、この方法で作成した <xref:System.DateTimeOffset> 値には、ローカル タイム ゾーンのオフセットが割り当てられます。  これは、文字リテラルを使用して割り当てられた <xref:System.DateTimeOffset> 値は、コードが別のコンピューターで実行されると、単一の時点の時刻を指すものではないことを意味しています。  
  
## DateTimeOffset コンストラクター  
 <xref:System.DateTimeOffset> 型は、6 つのコンストラクターを定義します。  そのうちの 4 つは、<xref:System.DateTime> コンストラクターに直接対応し、UTC からの日付と時刻のオフセットを定義する型 <xref:System.TimeSpan> の追加のパラメーターを提供します。  これにより、日付と時刻に関する各コンポーネントの値に基づいて、<xref:System.DateTimeOffset> 値を定義できます。  たとえば、次のコードでは 4 つのコンストラクターを使用して、7\/1\/2008 12:05 AM \+01:00 という同一の値を持つ <xref:System.DateTimeOffset> オブジェクトをインスタンス化します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]  
  
 コンストラクターに対する引数の 1 つである、<xref:System.Globalization.PersianCalendar> オブジェクトを使用してインスタンス化した <xref:System.DateTimeOffset> オブジェクトの値は、コンソールにはペルシャ暦ではなくグレゴリオ暦として表示されることに注意してください。  ペルシャ暦を使用した日付を出力するには、トピック「<xref:System.Globalization.PersianCalendar>」にある例を参照してください。  
  
 残りの 2 つのコンストラクターは、<xref:System.DateTime> 値から <xref:System.DateTimeOffset> オブジェクトを作成します。  このうちの 1 つのコンストラクターには、1 つのパラメーターがあります。このパラメーターを使用して、<xref:System.DateTime> 値を <xref:System.DateTimeOffset> 値に変換します。  結果として得られる <xref:System.DateTimeOffset> 値のオフセットは、コンストラクターの単一のパラメーターの <xref:System.DateTime.Kind%2A> プロパティに依存します。  その値が <xref:System.DateTimeKind?displayProperty=fullName> である場合、オフセットは <xref:System.TimeSpan.Zero?displayProperty=fullName> と等しい値に設定されます。  それ以外の場合は、オフセットはローカル タイム ゾーンの値と等しい値に設定されます。  次に、このコンストラクターを使用して、UTC およびローカル タイム ゾーンを表す <xref:System.DateTimeOffset> オブジェクトをインスタンス化する例を示します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]  
  
> [!NOTE]
>  単一の <xref:System.DateTime> パラメーターを持つ <xref:System.DateTimeOffset> コンストラクターのオーバーロードを呼び出すことは、<xref:System.DateTime> 値の <xref:System.DateTimeOffset> 値への暗黙の変換を実行することと同じです。  
  
 残りの 2 つのコンストラクターのうち、もう 1 つのコンストラクターは、<xref:System.DateTime> 値から <xref:System.DateTimeOffset> オブジェクトを作成します。この値には、変換する値である <xref:System.DateTime> と、UTC からの日付と時刻のオフセットを表す <xref:System.TimeSpan> の 2 つのパラメーターがあります。  このオフセット値は、コンストラクターの最初のパラメーターの <xref:System.DateTime.Kind%2A> プロパティに対応する必要があります。対応していないと、<xref:System.ArgumentException> がスローされます。  最初のパラメーターの <xref:System.DateTime.Kind%2A> プロパティが <xref:System.DateTimeKind?displayProperty=fullName> である場合、2 番目のパラメーターの値は <xref:System.TimeSpan.Zero?displayProperty=fullName> であることが必要です。  最初のパラメーターの <xref:System.DateTime.Kind%2A> プロパティが <xref:System.DateTimeKind?displayProperty=fullName> である場合、2 番目のパラメーターの値はローカル システムのタイム ゾーンのオフセットであることが必要です。  最初のパラメーターの <xref:System.DateTime.Kind%2A> プロパティが <xref:System.DateTimeKind?displayProperty=fullName> である場合、どのようなオフセットでも有効になります。  次のコードは、このコンストラクターを呼び出して <xref:System.DateTime> を <xref:System.DateTimeOffset> 値に変換する例を示したものです。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]  
  
## 暗黙の型変換  
 <xref:System.DateTimeOffset> 型は、<xref:System.DateTime> 値から <xref:System.DateTimeOffset> 値への暗黙の型変換をサポートします。暗黙の型変換とは、明示的なキャスト \(C\# の場合\) や明示的な変換 \(Visual Basic の場合\) を要求せず、かつ情報を失わずに、ある型を別の型に変換することを言います。  次に、コード例を示します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]  
  
 結果として得られる <xref:System.DateTimeOffset> 値のオフセットは、<xref:System.DateTime.Kind%2A?displayProperty=fullName> プロパティの値に依存します。  その値が <xref:System.DateTimeKind?displayProperty=fullName> である場合、オフセットは <xref:System.TimeSpan.Zero?displayProperty=fullName> と等しい値に設定されます。  値が <xref:System.DateTimeKind?displayProperty=fullName> または <xref:System.DateTimeKind?displayProperty=fullName> である場合、オフセットはローカル タイム ゾーンの値と等しい値に設定されます。  
  
## 日付と時刻の文字列形式の解析  
 <xref:System.DateTimeOffset> 型は、日付と時刻の文字列形式を <xref:System.DateTimeOffset> 値に変換する 4 つのメソッドをサポートしています。  
  
-   <xref:System.DateTimeOffset.Parse%2A> メソッド。日付と時刻の文字列形式を <xref:System.DateTimeOffset> 値に変換します。変換に失敗した場合には例外をスローします。  
  
-   <xref:System.DateTimeOffset.TryParse%2A> メソッド。日付と時刻の文字列形式を <xref:System.DateTimeOffset> 値に変換します。変換に失敗した場合には `false` を返します。  
  
-   <xref:System.DateTimeOffset.ParseExact%2A> メソッド。指定の形式での日付と時刻の文字列形式を <xref:System.DateTimeOffset> 値に変換します。  変換に失敗した場合には例外をスローします。  
  
-   <xref:System.DateTimeOffset.TryParseExact%2A> メソッド。指定の形式での日付と時刻の文字列形式を <xref:System.DateTimeOffset> 値に変換します。  変換に失敗した場合には `false` を返します。  
  
 次に、これらの 4 つの文字列変換メソッドを個別に呼び出して、<xref:System.DateTimeOffset> 値をインスタンス化する例を示します。  
  
 [!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
 [!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]  
  
## 参照  
 [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)