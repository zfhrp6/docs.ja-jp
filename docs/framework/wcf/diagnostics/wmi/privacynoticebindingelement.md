---
title: PrivacyNoticeBindingElement
ms.date: 03/30/2017
ms.assetid: 0cf110b1-e25b-4d67-986b-10cb04dc4826
ms.openlocfilehash: a4ae5153525d5468955a09d19e534c00114c6530
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485119"
---
# <a name="privacynoticebindingelement"></a>PrivacyNoticeBindingElement
PrivacyNoticeBindingElement  
  
## <a name="syntax"></a>構文  
  
```  
class PrivacyNoticeBindingElement : BindingElement  
{  
  sint32 PrivacyNoticeVersion;  
  string Url;  
};  
```  
  
## <a name="methods"></a>メソッド  
 PrivacyNoticeBindingElement クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 PrivacyNoticeBindingElement クラスには、次のプロパティがあります。  
  
### <a name="privacynoticeversion"></a>PrivacyNoticeVersion  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 プライバシーに関する声明のバージョンです。  
  
### <a name="url"></a>URL  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 プライバシーに関する声明がある URL です。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
