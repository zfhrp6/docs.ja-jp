---
title: "追加のクラス ライブラリと API"
ms.custom: 
ms.date: 04/12/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c22de3ed401e0be10b155649395da43cedb35e6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="additional-class-libraries-and-apis"></a>追加のクラス ライブラリと API

.NET Framework は、絶えず進化を続けています。クロスプラットフォーム開発を強化するために、またはお客様にいち早く新しい機能を紹介するために、マイクロソフトは新機能のアウトオブバウンド (OOB) をリリースします。 ここでは、ドキュメントが用意されている OOB プロジェクトの一覧を示します。  
  
さらに、いくつかのライブラリは、特定のプラットフォームまたは .NET Framework の実装を対象にしています。 たとえば、<xref:System.Text.CodePagesEncodingProvider>クラスは、コード ページ エンコーディングを .NET Framework を使用して開発された UWP アプリで利用できます。 ここでは、これらのライブラリの一覧も示します。  
  
## <a name="oob-projects"></a>OOB プロジェクト
  
| プロジェクト | 説明 |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | スレッド セーフであり、内容が変更されないことが保証されているコレクションを提供します。 |
| <xref:System.Net.Http.WinHttpHandler> | Windows の WinHTTP インターフェイスに基づいた <xref:System.Net.Http.HttpClient> のメッセージ ハンドラーを提供します。 |
| [System.Numerics.Vectors](https://msdn.microsoft.com/library/mt452176.aspx) | SIMD ハードウェア ベースのアクセラレータを利用できるベクター型のライブラリを提供します。| 
| <xref:System.Threading.Tasks.Dataflow> | TPL データフロー ライブラリはデータ フロー コンポーネントを提供し、同時実行対応アプリケーションの堅牢性を強化します。 |  

## <a name="platform-specific-libraries"></a>プラットフォーム固有のライブラリ
  
| プロジェクト | 説明 |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | 拡張、<xref:System.Text.EncodingProvider>コード ページ エンコーディングをユニバーサル Windows プラットフォームを対象とするアプリを利用できるようにするクラス。 |  
  
## <a name="private-apis"></a>プライベート API  

この API は製品インフラストラクチャをサポートします。コードから直接使用することはできません。  
  
| API 名 |
| -------- |
| [System.Net.Connection クラス](../../../docs/framework/additional-apis/connection.md) |
| [System.Net.Connection.m\_WriteList フィールド](../../../docs/framework/additional-apis/m_writelist.md) |
| [System.Net.ConnectionGroup クラス](../../../docs/framework/additional-apis/connectiongroup.md) |
| [System.Net.ConnectionGroup.m\_ConnectionList フィールド](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [System.Net.HttpWebRequest です。\_HttpResponse フィールド](../../../docs/framework/additional-apis/_httpresponse.md) |
| [System.Net.HttpWebRequest です。\_AutoRedirects フィールド](../../../docs/framework/additional-apis/_autoredirects.md) |
| [System.Net.ServicePoint.m\_ConnectionGroupList フィールド](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [System.Net.ServicePointManager.s\_ServicePointTable フィールド](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes フィールド](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [System.Windows.Forms.Design.DataMemberFieldEditor クラス](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [System.Windows.Forms.Design.DataMemberListEditor クラス](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a>関連項目

[NET Framework および特別なリリース](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)
