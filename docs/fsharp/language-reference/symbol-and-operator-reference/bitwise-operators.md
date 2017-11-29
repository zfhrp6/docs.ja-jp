---
title: "ビット処理演算子 (F#)"
description: "F# のプログラミング言語で使用可能なビットごとの演算子について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8a2c87f5-b4c7-47fe-8580-82c956f605e5
ms.openlocfilehash: 61a8e6bafe97a229480c967a4afb5d2a256474c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="bitwise-operators"></a>ビット処理演算子

このトピックでは、f# 言語で使用可能なビットごとの演算子について説明します。

## <a name="summary-of-bitwise-operators"></a>ビットごとの演算子の概要
次の表では、ボックス化解除された整数型の f# 言語でサポートされているビットごとの演算子について説明します。

|演算子|メモ|
|--------|-----|
|`&&&`|ビットごとの AND 演算子です。 結果のビットは、両方のソース オペランドの対応するビットが 1 の場合にのみ、値 1 を持ちます。|
|<code>&#124;&#124;&#124;</code>|ビットごとの OR 演算子。 いずれかに、結果のビットが 1 の値を持つソースに対応するビットのオペランドは 1 です。|
|`^^^`|ビットごとの排他的 OR 演算子。 結果のビットは、ソース オペランドのビットが等しくない値を持つ場合にのみ、値 1 を持ちます。|
|`~~~`|ビットごとの否定演算子です。 これは、単項演算子であり、ソース オペランド内のすべての 0 のビットが 1 のビットに変換し、すべて 1 ビットが 0 のビットに変換結果が生成されます。|
|`<<<`|ビットごとの左シフト演算子。 結果は、最初のオペランドのビットを 2 番目のオペランドのビット数だけ左にシフトします。 最下位の位置には、最上位の位置からシフトは循環しません。 最下位ビットが 0 で埋められます。 2 番目の引数の型は`int32`します。|
|`>>>`|ビットごと右シフト演算子。 結果は、最初のオペランドと 2 番目のオペランドのビット数だけ右にシフトするビットです。 最上位の位置には、最下位の位置からシフトは循環しません。 符号なし型の場合は、最上位ビットが 0 で埋められます。 署名された型の場合は、最上位ビットはものに埋められます。 2 番目の引数の型は`int32`します。|

ビットごとの演算子では、次の種類を使用できます: `byte`、 `sbyte`、 `int16`、 `uint16`、 `int32 (int)`、 `uint32`、 `int64`、 `uint64`、 `nativeint`、および`unativeint`です。

## <a name="see-also"></a>関連項目
[シンボルと演算子のリファレンス](index.md)

[算術演算子](arithmetic-operators.md)

[ブール演算子](boolean-operators.md)

