---
title: ServiceAuthorizationBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fd22cd7e7783a67e7ad10371533eee680bd3af16
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="serviceauthorizationbehavior"></a>ServiceAuthorizationBehavior
ServiceAuthorizationBehavior  
  
## <a name="syntax"></a>構文  
  
```  
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a>メソッド  
 ServiceAuthorizationBehavior クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 ServiceAuthorizationBehavior クラスには、次のプロパティがあります。  
  
### <a name="impersonatecallerforalloperations"></a>impersonateCallerForAllOperations  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 受信メッセージによって提供される資格情報を使用してサービスが偽装を試みるかどうかを制御する値。  
  
### <a name="principalpermissionmode"></a>PrincipalPermissionMode  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 サーバーでの操作を実行するために使用されるプリンシパル。  
  
### <a name="roleprovider"></a>RoleProvider  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 ASP.NET ロール プロバイダーの名前。  
  
### <a name="serviceauthorizationmanager"></a>ServiceAuthorizationManager  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 カスタム承認で使用される承認マネージャー。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
