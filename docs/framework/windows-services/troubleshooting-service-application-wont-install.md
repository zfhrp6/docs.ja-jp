---
title: 'トラブルシューティング: サービス アプリケーションをインストールできない場合'
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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509661"
---
# <a name="troubleshooting-service-application-won39t-install"></a><span data-ttu-id="d7ad6-102">トラブルシューティング: サービス アプリケーションをインストールできない場合</span><span class="sxs-lookup"><span data-stu-id="d7ad6-102">Troubleshooting: Service Application Won&#39;t Install</span></span>
<span data-ttu-id="d7ad6-103">サービス アプリケーションが正しくインストールされない場合は、サービス クラスの <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> プロパティが、そのサービスのインストーラーで示されているのと同じ値に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d7ad6-103">If your service application will not install correctly, check to make sure that the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for the service class is set to the same value as is shown in the installer for that service.</span></span> <span data-ttu-id="d7ad6-104">サービスが正しくインストールされるためには、両方のインスタンスで同じ値になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7ad6-104">The value must be the same in both instances in order for your service to install correctly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7ad6-105">また、インストール ログを見て、インストール プロセスについてのフィードバックを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="d7ad6-105">You can also look at the installation logs to get feedback on the installation process.</span></span>  
  
 <span data-ttu-id="d7ad6-106">同じ名前の別のサービスが既にインストールされているかどうかも確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7ad6-106">You should also check to determine whether you have another service with the same name already installed.</span></span> <span data-ttu-id="d7ad6-107">インストールが成功するには、サービス名が一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7ad6-107">Service names must be unique for installation to succeed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7ad6-108">参照</span><span class="sxs-lookup"><span data-stu-id="d7ad6-108">See Also</span></span>  
 [<span data-ttu-id="d7ad6-109">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="d7ad6-109">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
