---
title: "ServicePointManager.s_ServicePointTable フィールド"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type: apiref
api_name: System.Net.ServicePointManager.s_ServicePointTable
api_location: System.dll
api_type: Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2f12a8ba4d2b84e5b5d73d26199adf687a95a2df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="servicepointmanagersservicepointtable-field"></a>ServicePointManager.s\_ServicePointTable フィールド

`ServicePointManager.s_ServicePointTable`<xref:System.Collections.Hashtable> HTTP のアクティブな接続の一覧を格納している (<xref:System.Net.ServicePoint>s) で、<xref:System.AppDomain>です。

## <a name="syntax"></a>構文
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> `ServicePointManager.s_ServicePointTable`フィールドはプライベートであり、コード内で直接使用します。
> 
> Microsoft は、どのような状況下で、実稼働アプリケーションでこのフィールドの使用をサポートしていません。

## <a name="requirements"></a>要件

**Namespace:**<xref:System.Net>

**アセンブリ:**システム (System.dll)

**.NET framework のバージョン:** 2.0 から利用可能です。
