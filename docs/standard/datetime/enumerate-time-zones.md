---
title: "方法 : コンピューター上に存在するタイム ゾーンを列挙する | Microsoft Docs"
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
  - "列挙 (タイム ゾーンを) [.NET Framework]"
  - "タイム ゾーン [.NET Framework], 列挙"
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : コンピューター上に存在するタイム ゾーンを列挙する
指定されたタイム ゾーンを正しく処理するには、システムで使用できるタイム ゾーンについての情報が必要です。  Windows XP オペレーティング システムと Windows Vista オペレーティング システムは、この情報をレジストリに格納します。  しかし、世界中に存在するタイム ゾーンの総数は多く、レジストリに含まれている情報はそのサブセットにすぎません。  さらに、レジストリ自体が動的な構造であり、その内容は意図的に、または偶然に変更される可能性があります。  そのため、アプリケーションでは、特定のタイム ゾーンがシステム上に定義されていて使用できるものと常に想定することはできません。  タイム ゾーン情報を使用する多くのアプリケーションでは、最初の手順として、必要なタイム ゾーンがローカル システムで使用できることを確認するか、またはタイム ゾーンの一覧をユーザーに表示して選択を促します。  そのためには、ローカル システムで定義されているタイム ゾーンをアプリケーションで列挙する必要があります。  
  
> [!NOTE]
>  ローカル システムで定義されていない可能性のある特定のタイム ゾーンの存在に依存するアプリケーションは、そのタイム ゾーンに関する情報をシリアル化および逆シリアル化することで、タイム ゾーンを確実に存在させることができます。  その後、タイム ゾーンをリスト コントロールに追加して、アプリケーションのユーザーが選択できるようにします。  詳細については、「[方法 : 埋め込みリソースにタイム ゾーンを保存する](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)」および「[方法 : 埋め込みリソースからタイム ゾーンを復元する](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)」を参照してください。  
  
### ローカル システムに存在するタイム ゾーンを列挙するには  
  
1.  <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=fullName> メソッドを呼び出します。  メソッドは、<xref:System.TimeZoneInfo> オブジェクトのジェネリック <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> コレクションを返します。  コレクションのエントリは、<xref:System.TimeZoneInfo.DisplayName%2A> プロパティの順に並んでいます。  たとえば、次のようになります。  
  
     [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
     [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]  
  
2.  `foreach` ループ \(C\# の場合\) または `For Each`...`Next` ループ \(Visual Basic の場合\) を使用して、コレクション内の個々の <xref:System.TimeZoneInfo> オブジェクトを列挙し、各オブジェクトに対して必要な処理を実行します。  たとえば、次の例では、手順 1. で返された <xref:System.TimeZoneInfo> オブジェクトの <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> コレクションを列挙し、各タイム ゾーンの表示名の一覧をコンソールに表示します。  
  
     [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
     [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]  
  
### ローカル システムに存在するタイム ゾーンの一覧をユーザーに表示するには  
  
1.  <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=fullName> メソッドを呼び出します。  メソッドは、<xref:System.TimeZoneInfo> オブジェクトのジェネリック <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> コレクションを返します。  
  
2.  手順 1. で返されたコレクションを、Windows フォームの `DataSource` プロパティまたは ASP.NET のリスト コントロールに割り当てます。  
  
3.  ユーザーが選択した <xref:System.TimeZoneInfo> オブジェクトを取得します。  
  
 Windows アプリケーションでの例を次に示します。  
  
## 使用例  
 この例は、システムで定義されているタイム ゾーンをリスト ボックスに表示する Windows アプリケーションを起動します。  次に、ユーザーが選択したタイム ゾーン オブジェクトの <xref:System.TimeZoneInfo.DisplayName%2A> プロパティの値を含むダイアログ ボックスを表示します。  
  
 [!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
 [!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]  
  
 ほとんどのリスト コントロール \(<xref:System.Windows.Forms.ListBox?displayProperty=fullName> コントロールや <xref:System.Web.UI.WebControls.BulletedList?displayProperty=fullName> コントロールなど\) では、コレクションが <xref:System.Collections.IEnumerable> インターフェイスを実装していれば、オブジェクト変数のコレクションを `DataSource` プロパティに割り当てることができます \(ジェネリック <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> クラスはこれを実装しています\)。コレクション内の個々のオブジェクトを表示するために、コントロールはオブジェクトの `ToString` メソッドを呼び出して、オブジェクトを表すために使用される文字列を抽出します。  <xref:System.TimeZoneInfo> オブジェクトの場合、`ToString` メソッドは <xref:System.TimeZoneInfo> オブジェクトの表示名 \(<xref:System.TimeZoneInfo.DisplayName%2A> プロパティの値\) を返します。  
  
> [!NOTE]
>  リスト コントロールはオブジェクトの `ToString` メソッドを呼び出すので、コントロールに <xref:System.TimeZoneInfo> オブジェクトのコレクションを割り当てて、各オブジェクトの意味のある名前を表示させることができます。さらに、ユーザーが選択した <xref:System.TimeZoneInfo> オブジェクトも取得できます。  これにより、コレクション内の各オブジェクトの文字列を抽出し、文字列をコレクションに割り当て、そのコレクションをコントロールの `DataSource` プロパティに割り当て、ユーザーが選択した文字列を取得し、その文字列を使用して対象のオブジェクトを抽出するという手間をかける必要がなくなります。  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   System.Core.dll への参照をプロジェクトに追加する。  
  
-   次の名前空間をインポートする。  
  
     <xref:System> \(C\# コードの場合\)  
  
     <xref:System.Collections.ObjectModel>  
  
## 参照  
 [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)   
 [方法 : 埋め込みリソースにタイム ゾーンを保存する](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)   
 [方法 : 埋め込みリソースからタイム ゾーンを復元する](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)