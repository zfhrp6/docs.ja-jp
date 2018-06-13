---
title: ServicePointManager.s_ServicePointTable フィールド
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.s_ServicePointTable
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 5450a0cb3e5bd39a86365b16d372c7e573a43496
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351759"
---
# <a name="servicepointmanagersservicepointtable-field"></a>ServicePointManager.s\_ServicePointTable フィールド

`ServicePointManager.s_ServicePointTable` <xref:System.Collections.Hashtable> HTTP のアクティブな接続の一覧を格納している (<xref:System.Net.ServicePoint>s) で、<xref:System.AppDomain>です。

## <a name="syntax"></a>構文
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> `ServicePointManager.s_ServicePointTable`フィールドはプライベートであり、コード内で直接使用します。
> 
> Microsoft は、どのような状況下で、実稼働アプリケーションでこのフィールドの使用をサポートしていません。

## <a name="requirements"></a>要件

**Namespace:** <xref:System.Net>

**アセンブリ:** システム (System.dll)

**.NET framework のバージョン:** 2.0 から利用可能です。
