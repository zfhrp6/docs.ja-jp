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
# <a name="troubleshooting-service-application-won39t-install"></a><span data-ttu-id="12e10-102">トラブルシューティング: サービス アプリケーションの受注 &#39; t インストール</span><span class="sxs-lookup"><span data-stu-id="12e10-102">Troubleshooting: Service Application Won&#39;t Install</span></span>
<span data-ttu-id="12e10-103">場合は、サービス アプリケーションが正しくインストールされないことを確認する、<xref:System.ServiceProcess.ServiceBase.ServiceName%2A>サービス クラスのプロパティが同じ値にそのサービスのインストーラーが示されています。</span><span class="sxs-lookup"><span data-stu-id="12e10-103">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="12e10-104">値は、サービスを正しくインストールするために両方のインスタンスに同じにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="12e10-104">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12e10-105">また、インストール処理に関するフィードバックをインストール ログを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="12e10-105">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="12e10-106">既にインストールされている同じ名前の別のサービスがあるかどうかを決定するも確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="12e10-106">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="12e10-107">サービス名をインストールするのには一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="12e10-107">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12e10-108">参照</span><span class="sxs-lookup"><span data-stu-id="12e10-108">See Also</span></span>  
 [<span data-ttu-id="12e10-109">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="12e10-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
