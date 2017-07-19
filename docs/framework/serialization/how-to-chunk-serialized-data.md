---
title: "方法 : シリアル化されたデータをチャンクする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "バイナリ シリアル化, データのチャンク"
  - "バイナリ シリアル化, 例"
  - "シリアル化されたデータのチャンク"
  - "データのチャンク"
  - "大規模なデータ セットのチャンク"
  - "シリアル化, データのチャンク"
  - "シリアル化, 例"
ms.assetid: 22f1b818-7e0d-428a-8680-f17d6ebdd185
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 方法 : シリアル化されたデータをチャンクする
Web サービス メッセージ内で大きなデータ セットを送信すると、次の 2 つの問題が発生します。  
  
1.  シリアル化エンジンのバッファリングによるワーキング セット \(メモリ\) の巨大化  
  
2.  Base64 エンコーディングの実行後はサイズが 33% 増大することによる、帯域幅の過剰消費  
  
 これらの問題を解決するには、シリアル化と逆シリアル化を制御する <xref:System.Xml.Serialization.IXmlSerializable> インターフェイスを実装します。特に、<xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> メソッドと <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> メソッドを実装することで、データをチャンクします。  
  
### サーバー側チャンク処理を実装するには  
  
1.  サーバー コンピューター上で、Web メソッドが ASP.NET バッファリングを無効にし、<xref:System.Xml.Serialization.IXmlSerializable> を実装する型を返す必要があります。  
  
2.  <xref:System.Xml.Serialization.IXmlSerializable> を実装する型は、<xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> メソッド内でデータをチャンクします。  
  
### クライアント側の処理を実装するには  
  
1.  クライアント プロキシ上で <xref:System.Xml.Serialization.IXmlSerializable> を実装する型を返すように Web メソッドを変更します。<xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> を使用するとこの処理を自動化できますが、この方法はここでは説明しません。  
  
2.  チャンクされたデータ ストリームを読み込み、バイトをディスクに書き込むための <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> メソッドを実装します。この実装により、進行状況イベントも発生します。これは、プログレス バーなどのグラフィック コントロールに使用できます。  
  
## 使用例  
 次のコード例では、クライアント上で ASP.NET バッファリングを無効にする Web メソッドを示します。また、<xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> メソッドにおいてデータをチャンクする <xref:System.Xml.Serialization.IXmlSerializable> インターフェイスをクライアント側で実装する方法も示します。  
  
 [!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)]
 [!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]  
[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)]
[!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]  
[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)]
[!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]  
  
## コードのコンパイル  
  
-   このコードでは、<xref:System>、<xref:System.Runtime.Serialization>、<xref:System.Web.Services>、<xref:System.Web.Services.Protocols>、<xref:System.Xml>、<xref:System.Xml.Serialization>、および <xref:System.Xml.Schema> の各名前空間を使用しています。  
  
## 参照  
 [カスタムのシリアル化](../../../docs/framework/serialization/custom-serialization.md)