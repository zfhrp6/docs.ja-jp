---
title: "WriteOnly (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WriteOnly"
  - "vb.WriteOnly"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "write-only properties"
  - "WriteOnly keyword"
  - "sensitive data, protecting"
  - "properties [Visual Basic], write-only"
  - "sensitive data"
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# WriteOnly (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

プロパティに書き込みはできるが、読み込みはできないことを指定します。  
  
## 解説  
  
## 規則  
 **宣言コンテキスト。** `WriteOnly` は、モジュール レベルでのみ使用できます。  つまり、`WriteOnly` プロパティの宣言コンテキストは、クラス、構造体、またはモジュールであることが必要で、ソース ファイル、名前空間、プロシージャでは宣言できません。  
  
 プロパティは `WriteOnly` で宣言できますが、変数ではできません。  
  
## WriteOnly を使用する状況  
 値の設定はできるが、その値が何かを知ることができないようなコードが必要になる場合があります。  たとえば、何らかの登録番号やパスワードなど、それを設定した以外のコンポーネントからアクセスされないよう保護する必要のある重要情報です。  このような場合に、`WriteOnly` プロパティを使用して値を設定します。  
  
> [!IMPORTANT]
>  `WriteOnly` プロパティを定義して使用する際には、次のような方法で保護を強化するようにしてください。  
  
-   **オーバーライド。**プロパティがクラスのメンバーである場合は、既定で [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) に設定されるようにし、`Overridable` や `MustOverride` に宣言しないでください。  これにより、派生クラスでのオーバーライドによってアクセスが許可されてしまうのを防ぐことができます。  
  
-   **アクセス レベル。**プロパティの重要情報を 1 つ以上の変数に格納する場合は、変数を [Private](../../../visual-basic/language-reference/modifiers/private.md) で宣言して、他のコードからアクセスできないようにしてください。  
  
-   **暗号化。**重要情報はすべて、平文ではなく暗号化された形式で格納してください。  悪意のあるコードが、何らかの方法でメモリ内のその領域にアクセスできた場合でも、データを使用するのが非常に困難になります。  また、暗号化は重要情報をシリアル化する必要がある場合にも使用されます。  
  
-   **リセット。**プロパティが定義されたクラス、構造体、またはモジュールが終了するとき、重要情報を既定値またはその他の意味のない値にリセットしてください。  こうすることで、メモリのその領域へのアクセスが一般に解放されたときの保護を強化できます。  
  
-   **永続性。**重要情報は、できればディスクなどに保存しないようにしてください。  また、重要情報をクリップボードに書き込むのは避けてください。  
  
 `WriteOnly` 修飾子は次の構文で使用します。  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## 参照  
 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)   
 [Private](../../../visual-basic/language-reference/modifiers/private.md)   
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)