---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: e03f83927ec5aef7f916b2262c9c8cff1db68ac9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486474"
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
