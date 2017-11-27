---
title: MtomMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c5fd2858688634ee48a67b930755fc3ceebbebf8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="mtommessageencodingbindingelement"></a>MtomMessageEncodingBindingElement
MtomMessageEncodingBindingElement  
  
## <a name="syntax"></a>構文  
  
```  
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>メソッド  
 MtomMessageEncodingBindingElement クラスで定義されているメソッドはありません。  
  
## <a name="properties"></a>プロパティ  
 MtomMessageEncodingBindingElement クラスには、次のプロパティがあります。  
  
### <a name="encoding"></a>エンコード  
 データ型: string  
  
 アクセスの種類 : 読み取り専用  
  
 バインディングでメッセージの送信に使用される文字セット エンコーディング。  
  
### <a name="maxreadpoolsize"></a>MaxReadPoolSize  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を定義する整数です。  
  
### <a name="maxwritepoolsize"></a>MaxWritePoolSize  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 新しいライターを割り当てずに同時に送信可能なメッセージの数を定義する整数です。  
  
### <a name="readerquotas"></a>ReaderQuotas  
 データ型 : XmlDictionaryReaderQuotas  
  
 アクセスの種類 : 読み取り専用  
  
 リーダのクォータ。  
  
## <a name="requirements"></a>要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|Namespace|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
