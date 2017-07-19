---
title: "XmlDictionaryReaderQuotas | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# XmlDictionaryReaderQuotas
XmlDictionaryReaderQuotas  
  
## 構文  
  
```  
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## メソッド  
 XmlDictionaryReaderQuotas クラスで定義されるメソッドはありません。  
  
## プロパティ  
 XmlDictionaryReaderQuotas クラスには、次のプロパティがあります。  
  
### MaxArrayLength  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 許される最大配列長。  
  
### MaxBytesPerRead  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 1 回の読み取りで返すことができる最大バイト数。  
  
### MaxDepth  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 1 回の読み取りでの最大ネスト ノード深度。  
  
### MaxNameTableCharCount  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 テーブル名の最大文字数。  
  
### MaxStringContentLength  
 データ型 : sint32  
  
 アクセスの種類 : 読み取り専用  
  
 XML 要素のコンテンツで許可される最大文字数。  
  
## 要件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|------------------------------|  
|名前空間|root\\ServiceModel で定義|  
  
## 参照  
 <xref:System.Xml.XmlDictionaryReaderQuotas>   
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>