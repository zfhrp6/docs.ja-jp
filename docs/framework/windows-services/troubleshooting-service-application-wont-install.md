---
title: 'のトラブルシューティング: アプリケーションはサービス&#39;インストールできません。'
ms.date: 03/30/2017
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
author: ghogen
manager: douge
ms.openlocfilehash: 1f3e5674f9a52627efdc24d6c70c0ab16dcdbbbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-service-application-won39t-install"></a>のトラブルシューティング: アプリケーションはサービス&#39;インストールできません。
場合は、サービス アプリケーションが正しくインストールされないことを確認する、<xref:System.ServiceProcess.ServiceBase.ServiceName%2A>サービス クラスのプロパティが同じ値にそのサービスのインストーラーが示されています。 値は、サービスを正しくインストールするために両方のインスタンスに同じにする必要があります。  
  
> [!NOTE]
>  また、インストール処理に関するフィードバックをインストール ログを確認することができます。  
  
 既にインストールされている同じ名前の別のサービスがあるかどうかを決定するも確認する必要があります。 サービス名をインストールするのには一意である必要があります。  
  
## <a name="see-also"></a>関連項目  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
