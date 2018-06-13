---
title: ブール演算子 (F#)
description: F# のプログラミング言語で使用可能なブール演算子について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: f8516ceb531907400f98dc4226d2985d3119e9e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563429"
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
