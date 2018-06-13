---
title: HttpWebRequest._CoreResponse フィールド
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 3627c9bf0d72ccec3a0d6d9c7c89b62f83dcd4b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356200"
---
# <a name="httpwebrequestcoreresponse-field"></a>HttpWebRequest です。\_CoreResponse フィールド

`HttpWebRequest._CoreResponse` オブジェクトは、(どちらか、 [CoreResponseData](coreresponsedata.md)または<xref:System.Exception>) の HTTP 応答の解析結果を含むです。

## <a name="syntax"></a>構文
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> この API は、コード内で直接使用するものではありません。 代わりに、使用する必要があります、<xref:System.Diagnostics.DiagnosticSource>ネットワーク用のコードをフックします。 参照してください[DiagnosticSource ユーザーズ ガイド 』](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)です。
> 
> Microsoft は、どのような状況下で、実稼働アプリケーションでこのクラスの使用をサポートしていません。

## <a name="requirements"></a>要件

**Namespace:** <xref:System.Net>

**アセンブリ:** システム (System.dll)

**.NET framework のバージョン:** 2.0 から利用可能です。
