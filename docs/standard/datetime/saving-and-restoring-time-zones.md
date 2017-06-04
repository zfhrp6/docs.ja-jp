---
title: "タイム ゾーンの保存と復元 | Microsoft Docs"
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
  - "逆シリアル化 [.NET Framework], タイム ゾーン"
  - "復元 (タイム ゾーンを)"
  - "保存 (タイム ゾーンを)"
  - "シリアル化 [.NET Framework], タイム ゾーン"
  - "タイム ゾーン オブジェクト [.NET Framework], 逆シリアル化"
  - "タイム ゾーン オブジェクト [.NET Framework], 復元"
  - "タイム ゾーン オブジェクト [.NET Framework], 保存"
  - "タイム ゾーン オブジェクト [.NET Framework], シリアル化"
  - "タイム ゾーン [.NET Framework], 復元"
  - "タイム ゾーン [.NET Framework], 保存"
ms.assetid: 4028b310-e7ce-49d4-a646-1e83bfaf6f9d
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# タイム ゾーンの保存と復元
<xref:System.TimeZoneInfo> クラスは、レジストリを利用して、定義されているタイム ゾーン データを取得します。  ただし、レジストリは動的な構造です。  さらに、レジストリに格納されているタイム ゾーンの情報は、主として、現在の年の時刻の調整と変換を行うためにオペレーティング システムによって使用されます。  このため、正確なタイム ゾーン データに依存するアプリケーションには 2 つの大きな影響があります。  
  
-   アプリケーションが必要とするタイム ゾーンが、レジストリで定義されていない、レジストリで名前が変更されている、またはレジストリから削除されている可能性があります。  
  
-   レジストリで定義されているタイム ゾーンに、過去のタイム ゾーンの変換に必要な特定の調整ルールに関する情報が含まれない可能性があります。  
  
 <xref:System.TimeZoneInfo> クラスは、これらの制約に対処するため、タイム ゾーン データのシリアル化 \(保存\) と逆シリアル化 \(復元\) をサポートします。  
  
## タイム ゾーンのシリアル化と逆シリアル化  
 タイム ゾーン データのシリアル化と逆シリアル化によるタイム ゾーンの保存と復元に関係するメソッド呼び出しは 2 つだけです。  
  
-   <xref:System.TimeZoneInfo> オブジェクトをシリアル化するには、オブジェクトの <xref:System.TimeZoneInfo.ToSerializedString%2A> メソッドを呼び出します。  このメソッドはパラメーターを受け取らず、タイム ゾーン情報が格納された文字列を返します。  
  
-   シリアル化された文字列から <xref:System.TimeZoneInfo> オブジェクトを逆シリアル化するには、その文字列を `static` \(Visual Basic では `Shared`\) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=fullName> メソッドに渡します。  
  
## シリアル化と逆シリアル化のシナリオ  
 <xref:System.TimeZoneInfo> オブジェクトを文字列に保存 \(シリアル化\) し、後で使用するときに復元 \(逆シリアル化\) できると、<xref:System.TimeZoneInfo> クラスの実用性と柔軟性が向上します。  このセクションでは、シリアル化と逆シリアル化が最も役に立ついくつかの状況を調べます。  
  
### アプリケーションでのタイム ゾーン データのシリアル化と逆シリアル化  
 シリアル化されたタイム ゾーンは、必要に応じて文字列から復元できます。  レジストリから取得したタイム ゾーンが特定の日付範囲内の日時を正しく変換できない場合は、アプリケーションでこれを行うことがあります。  たとえば、Windows XP のレジストリのタイム ゾーン データは単一の調整規則をサポートしますが、Windows Vista のレジストリで定義されているタイム ゾーンは通常 2 つの調整規則についての情報を提供します。  つまり、過去の時刻変換が正しく行われない可能性があります。  タイム ゾーン データのシリアル化と逆シリアル化により、このような制約に対処できます。  
  
 次の例では、米国の中部標準時ゾーンが導入される前に 1883 ~ 1917 年まで米国東部標準時タイム ゾーンを表すように、調整規則のない <xref:System.TimeZoneInfo> のカスタム クラスを定義します。  このカスタム タイム ゾーンを、グローバル スコープを持つ変数にシリアル化します。  タイム ゾーン変換メソッド `ConvertUtcTime` に世界協定時刻 \(UTC\) を渡して変換します。  1917 年以前の日時の場合は、カスタム東部標準時ゾーンがシリアル化された文字列から復元されて、レジストリから取得されたタイム ゾーンの代わりに使用されます。  
  
 [!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
 [!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]  
  
### タイム ゾーンの例外の処理  
 レジストリは動的な構造なので、その内容は偶然に、または意図的に変更される可能性があります。  タイム ゾーンはレジストリで定義されている必要があり、アプリケーションの正常な実行に必要ですが、つまり、これが存在しなくなる可能性があります。  タイム ゾーンのシリアル化と逆シリアル化がサポートされていないと、<xref:System.TimeZoneNotFoundException> が発生した場合は、アプリケーションを終了してこれを処理するしか方法がありません。  一方、タイム ゾーンのシリアル化と逆シリアル化を使用すると、予期しない <xref:System.TimeZoneNotFoundException> が発生しても、シリアル化された文字列から必要なタイム ゾーンを復元することで対処でき、アプリケーションは実行を継続できます。  
  
 次の例では、カスタムの中部標準時ゾーンを作成してシリアル化します。  その後、レジストリから中部標準時ゾーンの取得を試みます。  取得操作で <xref:System.TimeZoneNotFoundException> または <xref:System.InvalidTimeZoneException> がスローされる場合は、例外ハンドラーがタイム ゾーンを逆シリアル化します。  
  
 [!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
 [!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]  
  
### シリアル化した文字列の格納と必要時の復元  
 前の例では、タイム ゾーン情報を文字列変数に格納し、必要ときはこれを復元しました。  ただし、シリアル化されたタイム ゾーン情報を格納している文字列自体は、外部ファイル、アプリケーションに埋め込まれたリソース ファイル、レジストリなどストレージ メディアに格納できます \(カスタム タイム ゾーンに関する情報は、レジストリではシステムのタイム ゾーン キーとは別に格納する必要があります\)。  
  
 シリアル化されたタイム ゾーン文字列をこの方法で格納すると、タイム ゾーン作成ルーチンもアプリケーション自体とは別になります。  たとえば、タイム ゾーン作成ルーチンは、アプリケーションが使用できる過去のタイム ゾーンの履歴情報を格納するデータ ファイルを実行および作成できます。  データ ファイルは、アプリケーションと共にインストールできます。また、アプリケーションでタイム ゾーンが必要になったときは、データ ファイルを開き、格納されている 1 つ以上のタイム ゾーンを逆シリアル化できます。  
  
 埋め込みリソースを使用してシリアル化されたタイム ゾーン データを格納する例については、「[方法 : 埋め込みリソースにタイム ゾーンを保存する](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)」および「[方法 : 埋め込みリソースからタイム ゾーンを復元する](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)」を参照してください。  
  
## 参照  
 [日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)