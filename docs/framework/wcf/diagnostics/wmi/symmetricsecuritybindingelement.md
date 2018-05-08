---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7fc720f4f0be25a0cec25d979942af8472efa4ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="symmetricsecuritybindingelement"></a>SymmetricSecurityBindingElement
SymmetricSecurityBindingElement  
  
## <a name="syntax"></a>構文  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a>メソッド  
 SymmetricSecurityBindingElement クラスで定義されるメソッドはありません。  
  
## <a name="properties"></a>プロパティ  
 SymmetricSecurityBindingElement クラスには、次のプロパティがあります。  
  
### <a name="messageprotectionorder"></a>MessageProtectionOrder  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 このバインディングのメッセージの暗号化と署名の命令。  
  
### <a name="requiresignatureconfirmation"></a>RequireSignatureConfirmation  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 バインディングで署名の確認が必要かどうか。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
