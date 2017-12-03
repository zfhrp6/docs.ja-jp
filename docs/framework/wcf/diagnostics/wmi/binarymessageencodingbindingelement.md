---
title: BinaryMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45f80b9ac7ca052ea3a8d7d89b35413b167eacfa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="binarymessageencodingbindingelement"></a>BinaryMessageEncodingBindingElement
BinaryMessageEncodingBindingElement  
  
## <a name="syntax"></a>構文  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>メソッド  
 BinaryMessageEncodingBindingElement クラスは、メソッドを一切定義しません。  
  
## <a name="properties"></a>プロパティ  
 BinaryMessageEncodingBindingElement クラスには、次のプロパティがあります。  
  
## <a name="maxreadpoolsize"></a>MaxReadPoolSize  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を定義する整数です。  
  
## <a name="maxsessionsize"></a>MaxSessionSize  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 エンコーディングに使用するバッファーのサイズ (バイト単位) を指定する値です。  
  
## <a name="maxwritepoolsize"></a>MaxWritePoolSize  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 新しいライターを割り当てずに同時に送信可能なメッセージの数を定義する整数です。  
  
## <a name="readerquotas"></a>ReaderQuotas  
 データ型 : XmlDictionaryReaderQuotas  
  
 アクセスの種類 : 読み取り専用  
  
 リーダのクォータ。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
