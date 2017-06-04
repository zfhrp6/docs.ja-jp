---
title: "接続のグループ化 | Microsoft Docs"
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
  - "インターネット、接続"
  - "接続 [.NET Framework]、グループ化"
  - "WebRequest クラス、接続のグループ化"
  - "ネットワーク リソース、接続"
  - "接続プール"
ms.assetid: 2ec502e8-4ba0-4c22-9410-f28eaf4eee63
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# 接続のグループ化
接続のグループは、フォームで定義した接続プールに一つのアプリケーション内の特定の要求を関連付けます。  これは、中間層アプリケーションによってユーザーに代わって後部サーバーに要求する接続し、Kerberos など\) または独自の資格情報を提供する次の例のように中間層アプリケーションによって、委任をサポートする認証プロトコルを使用します。  たとえば、ユーザーをその支払名簿の情報を表示する内部 Web サイトとします。健一郎してください。  健一郎を認証すると、支払名簿の情報を取得するために、中間層のアプリケーション サーバーは後部サーバーに接続するに健一郎の資格情報を使用します。  次に、スーザンは、サービス拠点を参照して、自分の支払名簿情報が必要です。  中間層アプリケーションが健一郎の資格情報を使用して既にを接続しているため、後部サーバーは、健一郎の情報と回答します。  ただし、アプリケーションで作成された接続のグループにユーザー名から後部サーバーに送信される各要求を割り当てると、各ユーザー別の接続プールに属していて、別のユーザーに誤って認証情報を共有することはできません。  
  
 特定の接続のグループに要求を割り当てるには、の <xref:System.Net.WebRequest> の <xref:System.Net.WebRequest.ConnectionGroupName%2A> のプロパティに要求する前に名前を割り当てる必要があります。  
  
## 参照  
 [接続の管理](../../../docs/framework/network-programming/managing-connections.md)   
 [方法: グループの接続にユーザー情報を割り当てる](../../../docs/framework/network-programming/how-to-assign-user-information-to-group-connections.md)