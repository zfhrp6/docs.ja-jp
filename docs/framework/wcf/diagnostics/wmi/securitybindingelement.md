---
title: SecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 5de844bc2741768e1b3c53278f20ad4900ffaac1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="securitybindingelement"></a>SecurityBindingElement
SecurityBindingElement  
  
## <a name="syntax"></a>構文  
  
```  
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## <a name="methods"></a>メソッド  
 SecurityBindingElement クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 SecurityBindingElement クラスには、次のプロパティがあります。  
  
### <a name="defaultalgorithmsuite"></a>DefaultAlgorithmSuite  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 バインディングで使用するアルゴリズムを指定します。  
  
### <a name="includetimestamp"></a>IncludeTimestamp  
 データ型 : boolean  
  
 アクセスの種類 : 読み取り専用  
  
 各メッセージにタイムスタンプが含まれるかどうかを指定するブール値です。  
  
### <a name="keyentropymode"></a>KeyEntropyMode  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 キーの作成に使用されるエントロピのソースです。  
  
### <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings  
 データ型 : LocalServiceSecuritySettings  
  
 アクセスの種類 : 読み取り専用  
  
 ローカル サービスに対するバインディング固有のセキュリティ プロパティです。  
  
### <a name="messagesecurityversion"></a>MessageSecurityVersion  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 メッセージ セキュリティで使用されるバージョンです。  
  
### <a name="securityheaderlayout"></a>SecurityHeaderLayout  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 このバインディングのセキュリティ ヘッダー内の要素の順序です。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>
