---
title: "アプリケーション開発での PNRP | Microsoft Docs"
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
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# アプリケーション開発での PNRP
Windows Vista では、ネットワーキング アプリケーションは、単純 PNRP のアプリケーション プログラミング インターフェイス \(API\) を使用して名前の書と決済機能にアクセスできます。  
  
## ピア名決済プロトコルの実行  
 簡単 PNRP API によって名前と住所を登録するには、クラウド明示的に指定されて; PNRP のコンポーネントが入力するに自動的に適切なクラウドとクラウド内の公開への住所が決まります。  
  
 Windows Vista の非常に簡単 PNRP 決済の名前については、PNRP の名前は getaddrinfo\(\) Windows ソケット機能に、連結されます。  IPv6 の住所に名前を決済するに PNRP を使用するには、アプリケーションは完全修飾ドメイン名 name.prnp \(FQDN\) を決済するには getaddrinfo\(\) 機能を使用できます。  名前が解決されるピア名である正味。  pnrp。  正味ドメインの名前は PNRP 決済の Windows Vista の引当ドメインです。  
  
 ピアツーピア アプリケーション間のメッセージ パッシングは、PeerChannel、WCF [大規模なデータおよびストリーミング](http://go.microsoft.com/fwlink/?LinkID=179652)などの基になるアーキテクチャによって行われます。  
  
## 参照  
 <xref:System.Net.PeerToPeer>