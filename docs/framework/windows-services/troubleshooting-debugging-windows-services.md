---
title: "Windows サービスをデバッグする場合 | Microsoft Docs"
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
  - "デバッグ [Visual Studio], Windows サービス"
  - "デバッグ (Windows サービス アプリケーションの)"
  - "サービス, デバッグ"
  - "サービス, トラブルシューティング"
  - "トラブルシューティング (デバッグ), Windows サービス"
  - "トラブルシューティング (サービス アプリケーション)"
  - "Windows サービス アプリケーション, デバッグ"
  - "Windows サービス アプリケーション, トラブルシューティング"
ms.assetid: cf859d4c-f04c-4cb7-81e3-bc7de8bea190
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 8
---
# Windows サービスをデバッグする場合
Windows サービス アプリケーションをデバッグするときには、サービスと **Windows サービス マネージャー**が対話します。  **サービス マネージャー**は、<xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドを呼び出してサービスを起動し、<xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドがリターンするのを 30 秒間待ちます。  この時間内にメソッドがリターンしない場合、マネージャーはサービス起動エラーを表示します。  
  
 「[方法 : Windows サービス アプリケーションをデバッグする](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)」で説明しているように、<xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドをデバッグするときには、この 30 秒のタイム リミットに注意してください。  <xref:System.ServiceProcess.ServiceBase.OnStart%2A> メソッドにブレークポイントを設定し、30 秒以内にそこを通過しなかった場合、マネージャーはサービスを起動しません。  
  
## 参照  
 [方法 : Windows サービス アプリケーションをデバッグする](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)   
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)