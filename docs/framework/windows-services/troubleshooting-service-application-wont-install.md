---
title: "トラブルシューティング: サービス アプリケーションの受注 &#39; t インストール"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 43c973d83d2d1b614cf0ce49ba8d4af24123b47e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-service-application-won39t-install"></a>トラブルシューティング: サービス アプリケーションの受注 &#39; t インストール
場合は、サービス アプリケーションが正しくインストールされないことを確認する、<xref:System.ServiceProcess.ServiceBase.ServiceName%2A>サービス クラスのプロパティが同じ値にそのサービスのインストーラーが示されています。 値は、サービスを正しくインストールするために両方のインスタンスに同じにする必要があります。  
  
> [!NOTE]
>  また、インストール処理に関するフィードバックをインストール ログを確認することができます。  
  
 既にインストールされている同じ名前の別のサービスがあるかどうかを決定するも確認する必要があります。 サービス名をインストールするのには一意である必要があります。  
  
## <a name="see-also"></a>参照  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
