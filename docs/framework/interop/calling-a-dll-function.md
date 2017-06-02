---
title: "DLL 関数の呼び出し | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "COM 相互運用機能, プラットフォーム呼び出し"
  - "DLL 関数"
  - "相互運用 (アンマネージ コードとの), プラットフォーム呼び出し"
  - "プラットフォーム呼び出し, 呼び出し (アンマネージ関数の)"
  - "アンマネージ関数"
  - "アンマネージ関数, 呼び出し"
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# DLL 関数の呼び出し
アンマネージ DLL 関数の呼び出しは、他のマネージ コードの呼び出しとほとんど同じですが、DLL 関数を十分理解するまでは混乱しやすい相違点があります。  このセクションでは、呼び出しに関連する特殊な問題について説明するトピックを示します。  
  
 プラットフォーム呼び出しから返される構造体は、マネージ コードとアンマネージ コードで同じ表現になるデータ型である必要があります。  このような型は、変換する必要がないため、*blittable 型*と呼ばれます \(「[Blittable 型と非 Blittable 型](../../../docs/framework/interop/blittable-and-non-blittable-types.md)」を参照してください\)。  戻り値の型が非 blittable 型の構造体である関数を呼び出すためには、非 blittable 型と同じサイズの blittable ヘルパー型を定義し、関数から制御が戻った後にデータを変換します。  
  
## このセクションの内容  
 [構造体の受け渡し](../../../docs/framework/interop/passing-structures.md)  
 定義済みレイアウトのデータ構造体を渡すときに生じる問題点を特定します。  
  
 [コールバック関数](../../../docs/framework/interop/callback-functions.md)  
 コールバック機能に関する基本的な情報を提供します。  
  
 [方法 : コールバック関数を実装する](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 マネージ コードにコールバック関数を実装する方法を説明します。  
  
## 関連項目  
 [アンマネージ DLL 関数の処理](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 プラットフォーム呼び出しを使ってアンマネージ DLL 関数を呼び出す方法を説明します。  
  
 [プラットフォーム呼び出しによるデータのマーシャリング](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 メソッドのパラメーターの宣言方法と、アンマネージ ライブラリによってエクスポートされる関数に引数を渡す方法について説明します。