---
title: "ブール演算子 (F#)"
description: "F# のプログラミング言語で使用可能なブール演算子について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f79370b8-4bc2-4704-b514-d392c80942bd
ms.openlocfilehash: 63588f2e371bf2c0f15de0b8a26a46be82f832c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="boolean-operators"></a>ブール演算子

このトピックでは、f# 言語でブール演算子のサポートについて説明します。


## <a name="summary-of-boolean-operators"></a>ブール演算子の概要
次の表は、f# 言語で使用可能なブール演算子をまとめたものです。 これらの演算子でサポートされる唯一の型は、`bool`型です。

|演算子|説明|
|--------|-----------|
|`not`|論理否定|
|<code>&#124;&#124;</code>|論理 OR|
|`&&`|ブール型の AND|

ブール値の AND および OR 演算子を実行*ショート サーキット評価*演算子の右側の式の評価、つまり、式の全体的な結果を決定する必要がある場合にのみです。 2 番目の式、`&&`に最初の式が評価された場合にのみ、演算子が評価される`true`; の 2 番目の式、`||`に最初の式が評価された場合にのみ、演算子が評価される`false`です。

## <a name="see-also"></a>関連項目
[ビット処理演算子](bitwise-operators.md)

[算術演算子](arithmetic-operators.md)

[シンボルと演算子のリファレンス](index.md)
