---
title: DLL 関数の呼び出し
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98d363b6c0838ff1211d969391f04ce8ccddd003
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387134"
---
# <a name="calling-a-dll-function"></a>DLL 関数の呼び出し
アンマネージ DLL 関数の呼び出しは、他のマネージ コードの呼び出しとほとんど同じですが、最初のうちは DLL 関数がわかりづらいと感じる違いがあります。 ここでは、通常とは異なる呼び出しに関連するいくつかの問題について説明しているトピックを紹介します。  
  
 プラットフォーム呼び出しから返される構造体は、マネージ コードとアンマネージ コードで同じ表現のデータ型である必要があります。 このような型のことは *blittable 型*と呼ばれます。これは、会話が必要ではないためです (「[Blittable and Non-Blittable Types](../../../docs/framework/interop/blittable-and-non-blittable-types.md)」(blittable 型と非 blittable 型) を参照してください)。 戻り値の型が非 blittable 構造体の関数を呼び出すには、非 blittable 型と同じサイズの blittable ヘルパー型を定義し、関数からデータが返された後にそのデータを変換します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [構造体の受け渡し](../../../docs/framework/interop/passing-structures.md)  
 事前に定義されたレイアウトを使用して、データ構造体の受け渡しに関する問題を特定します。  
  
 [コールバック関数](../../../docs/framework/interop/callback-functions.md)  
 コールバック関数に関する基本情報を提供します。  
  
 [方法: コールバック関数を実装する](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 マネージ コードにコールバック関数を実装する方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [アンマネージ DLL 関数の処理](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 プラットフォーム呼び出しを使用して、アンマネージ DLL 関数を呼び出す方法について説明します。  
  
 [プラットフォーム呼び出しによるデータのマーシャリング](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 メソッドのパラメーターを宣言してアンマネージ ライブラリによってエクスポートされた関数に引数を渡す方法について説明します。
