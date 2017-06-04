---
title: "System.Net.PeerToPeer.Collaboration 名前空間について | Microsoft Docs"
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
ms.assetid: b5d8c1c1-6844-4947-9759-c7f1b564bded
caps.latest.revision: 4
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 4
---
# System.Net.PeerToPeer.Collaboration 名前空間について
<xref:System.Net.PeerToPeer.Collaboration> の名前空間がピアツーピア コラボレーションの下部組織を使用してピアのコラボレーション活動を実行するために使用されるおよびクラス API を提供します。  
  
## クラス  
 コラボレーション ピアツーピア活動の実装に使用される主類は次のとおりです:  
  
-   ピアの取引連絡先を保存するために使用できる <xref:System.Net.PeerToPeer.Collaboration.ContactManager>。  
  
-   ゲーム チャット、のクライアントまたは協議ソリューションなど、連携して動作する <xref:System.Net.PeerToPeer.Collaboration.PeerApplication>。  
  
-   活動で協力するピア。  これらの <xref:System.Net.PeerToPeer.Collaboration.PeerContact>ピアは、<xref:System.Net.PeerToPeer.Collaboration.PeerNearMe>、または <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> の対象として表すことができます。  
  
-   どのアプリケーションを使用できるように、どのピアは、参加するかを指定する <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> の静的なクラス自体。  
  
 <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> 方法がコラボレーション セッションにピアを依頼するために使用されます。  ピア呼び出しの信号にアプリケーションは、コラボレーションのセッションで提携するオブジェクト、プレゼンス情報を更新するイベントの別のピアに配属できます。  すべての入力がピアに割り当てるか指定するにプレゼンスのクラスが <xref:System.Net.PeerToPeer.Collaboration.Peer> がコラボレーションに使用できる、<xref:System.Net.PeerToPeer.Collaboration.PeerScope> のクラスを使用していますかどうかを指定します: <xref:System.Net.PeerToPeer.Collaboration.PeerScope> \(グローバル\)、<xref:System.Net.PeerToPeer.Collaboration.PeerScope>、\(サブネット\) または <xref:System.Net.PeerToPeer.Collaboration.PeerScope>。  
  
 コラボレーションのセッションは、4 種類の手順で構成されます:  
  
-   検出。  ピア、アプリケーションやプレゼンス情報を見つけたまたは配分します。  たとえば、同じゲームをインストールする保管場所のサブネットの他の従業員を検索します。  
  
-   招待状。  <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> セッションを開始、または入力するリモート ピアの安全な招待状を送信、承認します。  
  
-   連絡先の管理。  検出された <xref:System.Net.PeerToPeer.Collaboration.ContactManager>に取引連絡先としてピアを追加します。  
  
-   通信。  通信を確立されると、<xref:System.Net> API、<xref:System.Net.PeerToPeer> API を使用すると、Windows Communication Foundation ピアのチャンネルは複数政党制通信用の分類されます。  
  
 たとえば、ホストのピアは、コラボレーション セッションを開始し、ホスト ピアの連絡先のマネージャに保管場所のピアのリモート ピアと 1 追加するに <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> 方法を使用します。  3 人のユーザーが自分のプライベート コラボレーションのセッションに加わります。  
  
 一般的な P2P のアプリケーションは次のとおりです: 関連の注記がまたは whiteboarding の電話会議、serverless チャット、アプリケーションの対話な広告、オンライン賭博セッション。  
  
## 参照  
 <xref:System.Net.PeerToPeer.Collaboration>