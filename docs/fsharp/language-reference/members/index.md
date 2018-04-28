---
title: メンバー (F#)
description: F# のプログラミング言語でオブジェクトのメンバーについて説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: a37f14d138cc017cf78e3a0ff1d5b5bba2f09020
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="members"></a>メンバー

このセクションでは、F# オブジェクト型のメンバーについて説明します。


## <a name="remarks"></a>コメント
*メンバー*は、型定義の一部の機能であり、`member`キーワードを使用して宣言されます。 レコード、クラス、判別共用体、インターフェイス、構造体などの F# オブジェクト型がメンバーをサポートします。 詳細については、「[レコード](../records.md)」、「[クラス](../classes.md)」、「[判別共用体](../discriminated-Unions.md)」、「[インターフェイス](../interfaces.md)」、および「[構造体](../structures.md)」を参照してください。

メンバーは通常、型のパブリック インターフェイスを構成するので、特に指定しない限りパブリックになります。 プライベートまたは内部としてメンバーを宣言することもできます。 詳細については、「[Access Control](../access-Control.md)」(アクセス制御) を参照してください。 型のシグネチャを使用して、型の特定のメンバーを公開するか公開しないこともできます。 詳細については、「[シグネチャ](../signatures.md)」を参照してください。

クラスでのみ使用されるプライベート フィールドと `do` バインドは、パブリック インターフェイスの一部ではなく、`member` キーワードを使用して宣言されないので、真のメンバーではありませんが、このセクションではそれらについても説明します。


## <a name="related-topics"></a>関連トピック


|トピック|説明|
|-----|-----------|
|[クラス内の `let` バインド](let-bindings-in-classes.md)|クラス内のプライベート フィールドと関数の定義について説明します。|
|[クラス内の `do` バインド](do-bindings-in-classes.md)|オブジェクトの初期化コードの仕様について説明します。|
|[プロパティ](properties.md)|クラスのプロパティ メンバーとその他の型について説明します。|
|[インデックス付きプロパティ](indexed-properties.md)|クラスの配列に似たプロパティとその他の型について説明します。|
|[メソッド](methods.md)|型のメンバーである関数について説明します。|
|[コンストラクター](constructors.md)|型のオブジェクトを初期化する特別な関数について説明します。|
|[演算子のオーバーロード](../operator-overloading.md)|型のカスタマイズした演算子の定義について説明します。|
|[イベント](events.md)|F# のイベントおよびイベント処理のサポートの定義について説明します。|
|[明示的なフィールド: `val` キーワード](explicit-fields-the-val-keyword.md)|型の初期化されていないフィールドの定義について説明します。|
