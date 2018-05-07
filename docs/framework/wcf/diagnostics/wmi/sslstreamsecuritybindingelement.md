---
title: SslStreamSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 18130d50-8996-4257-9c60-bc457f8654d8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 75e85cad482e19dcdc8c472df250c5595461085f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sslstreamsecuritybindingelement"></a>SslStreamSecurityBindingElement
SslStreamSecurityBindingElement  
  
## <a name="syntax"></a>構文  
  
```  
class SslStreamSecurityBindingElement : BindingElement  
{  
  boolean RequireClientCertificate;  
};  
```  
  
## <a name="methods"></a>メソッド  
 SslStreamSecurityBindingElement クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 SslStreamSecurityBindingElement クラスには、次のプロパティがあります。  
  
### <a name="requireclientcertificate"></a>RequireClientCertificate  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 このバインディングにクライアント証明書が必要かどうかを指定します。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
