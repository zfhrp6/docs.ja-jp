---
title: 1025 - BookmarkScopeInitialized
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63584434-e709-471d-9e96-97d3d99e70d6
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9aec874ea3c93878e519eb691a99f415a4810709
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="1025---bookmarkscopeinitialized"></a>1025 - BookmarkScopeInitialized
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|1025|  
|キーワード|WFRuntime|  
|レベル|詳細|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  
 BookmarkScope が初期化されていることを示します。  
  
## <a name="message"></a>メッセージ  
 TemporaryId: '%1' を指定されていた BookmarkScope が ID: '%2' で初期化されました。  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|TemporaryId|xs:string|ブックマークの一時 ID。|  
|InitializedId|xs:string|ブックマークの初期化された ID。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
