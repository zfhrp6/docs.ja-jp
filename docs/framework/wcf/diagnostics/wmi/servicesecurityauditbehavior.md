---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 3adc721dd8ad0fb706e172373e5da70fe6032db6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
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
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
