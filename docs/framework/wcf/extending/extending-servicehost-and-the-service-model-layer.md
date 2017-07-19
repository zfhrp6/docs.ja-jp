---
title: "ServiceHost とサービス モデル レイヤーの拡張 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "サービス モデルの拡張 [WCF]"
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# ServiceHost とサービス モデル レイヤーの拡張
サービス モデル レイヤーは、基になるチャネルから受信メッセージをプルし、そのメッセージをアプリケーション コードでのメソッド呼び出しに変換し、結果を呼び出し元に送信する役割があります。サービス モデル拡張は、クライアントやディスパッチャーの機能、カスタム動作、メッセージとパラメーターの途中受信、およびその他の拡張機能に関連する実行や通信の動作と機能を変更または実装します。  
  
## このセクションの内容  
 [クライアントの拡張](../../../../docs/framework/wcf/extending/extending-clients.md)  
 クライアント ランタイムを途中受信して変更できるインターフェイス、およびクライアント アプリケーションのカスタム拡張を挿入できるクラスについて説明します。たとえば、カスタム クライアント メッセージ ログやカスタム メッセージ シリアル化などを実行できます。  
  
 [ディスパッチャーの拡張](../../../../docs/framework/wcf/extending/extending-dispatchers.md)  
 サービス ランタイムを途中受信して変更できるインターフェイス、およびサービス アプリケーションのカスタム拡張を挿入できるクラスについて説明します。たとえば、カスタム サービス ログ、サービス側でのメッセージ検証、カスタム ディスパッチなどを実行できます。  
  
 [拡張可能オブジェクト](../../../../docs/framework/wcf/extending/extensible-objects.md)  
 5 つの拡張可能オブジェクトと、<xref:System.ServiceModel.IExtensibleObject%601> パターンについて説明します。拡張可能オブジェクト パターンは、既存のランタイム クラスに新しい機能を付加して拡張したり、オブジェクトに新しい状態を追加するために使用します。このようなオブジェクトを実際に拡張することにより、処理の段階に応じて、共通の拡張可能オブジェクトに定義された共有の状態や機能にアクセスすることができます。  
  
 [動作を使用したランタイムの構成と拡張](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ランタイムで設定を変更したり、拡張機能を挿入したりするには、動作を使用します。WCF には、調整機能、インスタンス化、およびサービスと操作に関するその他のさまざまな側面を制御するための、システムに実装済みの動作が用意されています。ここでは、独自のカスタム動作を作成し、プログラムおよび構成ファイルにより、作成したカスタム動作を使用できるようにする方法について説明します。  
  
 [ServiceHostFactory を使用したホストの拡張](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 <xref:System.ServiceModel.ServiceHostBase?displayProperty=fullName> および <xref:System.ServiceModel.ServiceHost?displayProperty=fullName> を拡張し、<xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=fullName> クラスを使用してホスト環境をカスタマイズする方法について説明します。  
  
## 関連項目  
  
## 関連項目