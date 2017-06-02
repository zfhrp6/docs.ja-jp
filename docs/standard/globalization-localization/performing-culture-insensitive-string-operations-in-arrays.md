---
title: "カルチャを認識しない配列の操作の実行 | Microsoft Docs"
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
  - "配列 [.NET Framework], カルチャを認識しない文字列操作"
  - "comparer パラメーター"
  - "カルチャを認識しない文字列操作, 配列で"
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# カルチャを認識しない配列の操作の実行
<xref:System.Array.Sort%2A?displayProperty=fullName> メソッドおよび <xref:System.Array.BinarySearch%2A?displayProperty=fullName> メソッドのオーバーロードは、既定では <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=fullName> プロパティを使用してカルチャを認識する並べ替えを実行します。  これらのメソッドによって返されるカルチャを認識する結果は、並べ替えの順序が異なるため、カルチャごとに異なる可能性があります。  カルチャに依存する動作が行われないようにするには、`comparer` パラメーターを受け付けるこのメソッドのオーバーロードを使用します。  `comparer` パラメーターは、配列内の要素を比較するときに使用する <xref:System.Collections.IComparer> の実装を指定します。  このパラメーターには、<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> を使用するカスタム インバリアント比較子クラスを指定します。  カスタム インバリアント比較子クラスの例については、「[カルチャを認識しないコレクションの操作の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)」の「SortedList クラスの使用」を参照してください。  
  
 **メモ** 比較メソッドに **CultureInfo.InvariantCulture** を渡すと、カルチャに依存しない比較が実行されます。  ただし、この場合、ファイル パス、レジストリ キー、環境変数などに関する非言語的な比較は行われません。  また、比較結果に基づくセキュリティの決定もサポートされません。  非言語的な比較を行う場合、または結果に基づくセキュリティの決定をサポートする場合は、<xref:System.StringComparison> 値を受け取る比較メソッドを使用し、  <xref:System.StringComparison> を渡す必要があります。  
  
## 参照  
 <xref:System.Array.Sort%2A?displayProperty=fullName>   
 <xref:System.Array.BinarySearch%2A?displayProperty=fullName>   
 <xref:System.Collections.IComparer>   
 [カルチャを認識しない文字列操作の実行](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)