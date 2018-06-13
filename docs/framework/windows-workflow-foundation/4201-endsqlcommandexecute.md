---
title: 4201 - EndSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: ae0dbc15-f98c-4096-a8d9-fbe4dc36f1cd
ms.openlocfilehash: 75c1cdd10aca6b177911bd9d2f51468016eb9e15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510222"
---
# <a name="4201---endsqlcommandexecute"></a>4201 - EndSqlCommandExecute
## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|ID|4201|  
|キーワード|WFInstanceStore|  
|レベル|詳細|  
|チャネル|Microsoft-Windows-Application Server-Applications/Debug|  
  
## <a name="description"></a>説明  
 SQL コマンドの実行が完了したことを示します。  
  
## <a name="message"></a>メッセージ  
 SQL コマンドの実行を終了します: %1  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|説明|  
|--------------------|--------------------|-----------------|  
|SqlCommand|xs:string|実行された SQL コマンド。|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
