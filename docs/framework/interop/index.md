---
title: "アンマネージ コードとの相互運用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f475877bcb7a794d1a58ef9202735e016363678b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="interoperating-with-unmanaged-code"></a>アンマネージ コードとの相互運用
.NET Framework は、COM コンポーネント、COM+ サービス、外部のタイプ ライブラリ、各種のオペレーティング システム サービスとの相互運用を促進します。 データ型、メソッド署名、およびエラー処理機構は、マネージ オブジェクト モデルとアンマネージ オブジェクト モデルでは異なります。 .NET Framework コンポーネントとアンマネージ コードの間の相互運用を簡素化し、移行パスを簡単にするために、共通言語ランタイムがクライアントとサーバーの両方からこれらのオブジェクト モデルの違いを隠します。  
  
 ランタイムの制御下で実行されるコードは、マネージ コードと呼ばれます。 逆に、ランタイムの外部で実行されるコードはアンマネージ コードと呼ばれます。 アンマネージ コードの例としては、COM コンポーネント、ActiveX インターフェイス、Win32 API 関数があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [アンマネージ コードとの相互運用性に関する方法](http://msdn.microsoft.com/en-us/ec21c6e1-e233-4cd9-95ae-b9b9cf807f9d)  
 アンマネージ コードとの相互運用の概念に関するドキュメントに用意されているすべての方法トピックへのリンクを示します。  
  
 [.NET Framework への COM コンポーネントの公開](../../../docs/framework/interop/exposing-com-components.md)  
 .NET Framework アプリケーションから COM コンポーネントを使用する方法について説明します。  
  
 [COM への .NET Framework コンポーネントの公開](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 COM アプリケーションから .NET Framework コンポーネントを使用する方法について説明します。  
  
 [アンマネージ DLL 関数の処理](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 プラットフォーム呼び出しを使用して、アンマネージ DLL 関数を呼び出す方法について説明します。  
  
 [相互運用のためのデザインの考慮事項](http://msdn.microsoft.com/en-us/b59637f6-fe35-40d6-ae72-901e7a707689)  
 統合 COM コンポーネントを記述するためのヒントを示します。  
  
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)  
 COM 相互運用機能とプラットフォーム呼び出しのマーシャリングについて説明します。  
  
 [方法: HRESULT に例外を割り当てる](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)  
 例外と HRESULT の間のマッピングについて説明します。  
  
 [ジェネリック型を使用する相互運用](http://msdn.microsoft.com/en-us/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 COM 相互運用で使用する場合の、ジェネリック型の動作について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [高度な COM 相互運用性](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 .NET Framework アプリケーションに COM コンポーネントを組み込む方法についての詳細情報へのリンクを示します。
