---
title: "サービス アプリケーションをインストールできない場合 | Microsoft Docs"
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
  - "サービス, デバッグ"
  - "サービス, トラブルシューティング"
  - "トラブルシューティング (NT サービス)"
  - "トラブルシューティング (サービス アプリケーション)"
  - "Windows NT サービス, トラブルシューティング"
  - "Windows サービス アプリケーション, トラブルシューティング"
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 8
---
# サービス アプリケーションをインストールできない場合
サービス アプリケーションが正しくインストールされない場合は、サービス クラスの <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> プロパティに、そのサービスのインストーラーに表示される値と同じ値が設定されているかどうかを確認します。  サービスを正しくインストールするには、これらの両方に同じ値を設定する必要があります。  
  
> [!NOTE]
>  インストール ログでインストール プロセスの情報を参照することもできます。  
  
 同名のサービスが既にインストールされているかどうかを調べる必要もあります。  サービスをインストールするには、サービス名が一意であることが必要です。  
  
## 参照  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)