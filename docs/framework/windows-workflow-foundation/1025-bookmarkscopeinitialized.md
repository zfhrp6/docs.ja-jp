---
title: 1025 - BookmarkScopeInitialized
ms.date: 03/30/2017
ms.assetid: 63584434-e709-471d-9e96-97d3d99e70d6
ms.openlocfilehash: ddc9b48120b9d31f71bfc99fff19ef252b08e295
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509588"
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
