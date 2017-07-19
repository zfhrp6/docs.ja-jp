---
title: "Windows ストア アプリのネットワーク分離 | Microsoft Docs"
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
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
caps.latest.revision: 7
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 7
---
# Windows ストア アプリのネットワーク分離
<xref:System.Net>、<xref:System.Net.Http>と <xref:System.Net.Http.Headers> の名前空間のクラスは、Windows の店舗または apps デスクトップ アプリケーションを作成することもできます。  Windows の app 店舗で使用される場合、これらの名前空間のクラスが [!INCLUDE[win8](../../../includes/win8-md.md)]に、ネットワーク上、それぞれ、アプリケーション セキュリティ モデルのコンポーネントによって使用される変化します。  適切なネットワークの機能は、システムの Windows app 店舗の app のマニフェスト ネットワークにアクセスできるように有効にする必要があります。  
  
## ネットワーク、それぞれのチェックリスト  
 ネットワークのそれぞれが Windows の店舗 app にコンフィギュレーションされていることを確認するには、このチェックリストを使用します。  
  
1.  app が必要とするネットワーク アクセスの方向を決定します。  これは出庫のクライアント開始された要求になります。また、受信した未承諾の要求がその両方のネットワークで要求タイプの組み合わせにすることができます。  
  
2.  その app が通信ネットワーク リソース タイプを定義します。  app はホームの信頼されたリソースと通信するか、ネットワークを証明する必要があります。  app は、インターネットでのリソースと通信する必要があります。  app が必要です。両方のタイプのネットワーク リソースへのアクセスをことがあります。  
  
3.  app のマニフェストの必要な最小ネットワーキングの分離の機能をコンフィギュレーションします。  
  
4.  、の app を展開し、修復に提供されているネットワーク、それぞれのツールを使用して、をテストするに移動します。  
  
 ネットワーク、それぞれのトラブルシューティングするために使用するネットワークの機能と分離のツールをコンフィギュレーションする方法の詳細については [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] の開発者ドキュメント参照 [ネットワーク、それぞれの機能をコンフィギュレーションする方法](http://go.microsoft.com/fwlink/?LinkID=228265) してください。  
  
## 参照  
 [Web サービスへの接続](http://go.microsoft.com/fwlink/?LinkID=245696)   
 [ネットワーク、それぞれのガイドラインとチェックリスト](http://go.microsoft.com/fwlink/?LinkID=228265)   
 [: Quickstart HttpClient を使用して接続](http://go.microsoft.com/fwlink/?LinkId=245697)   
 [HttpClient のハンドラーの使用方法](http://go.microsoft.com/fwlink/?LinkId=245699)   
 [HttpClient の接続を保護する方法](http://go.microsoft.com/fwlink/?LinkId=245698)   
 [サンプルの HttpClient](http://go.microsoft.com/fwlink/?LinkId=242550)