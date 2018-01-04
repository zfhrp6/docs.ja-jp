---
title: ServiceSecurityAuditBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: ea9c04c201ff022fcea54b81a998b7020fb2a836
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="servicesecurityauditbehavior"></a>ServiceSecurityAuditBehavior
ServiceSecurityAuditBehavior  
  
## <a name="syntax"></a>構文  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a>メソッド  
 ServiceSecurityAuditBehavior クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 ServiceSecurityAuditBehavior クラスには、次のプロパティがあります。  
  
### <a name="auditloglocation"></a>AuditLogLocation  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 監査ログの場所。  
  
### <a name="messageauthenticationauditlevel"></a>MessageAuthenticationAuditLevel  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 監査イベントをログに記録するために使用されるメッセージ認証レベルの種類。  
  
### <a name="serviceauthorizationauditlevel"></a>ServiceAuthorizationAuditLevel  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 監査ログに記録される承認イベントの種類。  
  
### <a name="suppressauditfailure"></a>SuppressAuditFailure  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 監査ログへの書き込みエラーを非表示にする動作を指定するブール型の値。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
