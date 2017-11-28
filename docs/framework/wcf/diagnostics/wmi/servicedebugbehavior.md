---
title: ServiceDebugBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2d6b866c90e3e6c6e72dc75f230bcf7b4e03a6bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="servicedebugbehavior"></a>ServiceDebugBehavior
ServiceDebugBehavior  
  
## <a name="syntax"></a>構文  
  
```  
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a>メソッド  
 ServiceDebugBehavior クラスで定義されるメソッドはありません。  
  
## <a name="properties"></a>プロパティ  
 ServiceDebugBehavior クラスには、次のプロパティがあります。  
  
### <a name="httphelppageenabled"></a>HttpHelpPageEnabled  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 `HttpGetUrl` 属性によって制御されるアドレスで、サービスが WSDL を公開するかどうかを制御します。  
  
### <a name="httphelppageurl"></a>HttpHelpPageUrl  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 HTTP を使用した取得のために、サービス WSDL が公開される場所を設定します。  
  
### <a name="httpshelppageenabled"></a>HttpsHelpPageEnabled  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 `HttpsGetUrl` 属性によって制御されるアドレスで、サービスが HTTPS を介して WSDL を公開するかどうかを制御します。  
  
### <a name="httpshelppageurl"></a>HttpsHelpPageUrl  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 HTTPS を使用した取得のために、サービス WSDL が公開される場所を設定します。  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 デバッグの目的でクライアントに返される SOAP エラーの詳細に、マネージ例外情報を含めるかどうかを指定します。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
