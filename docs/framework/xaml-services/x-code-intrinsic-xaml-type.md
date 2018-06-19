---
title: 'x:Code 組み込み XAML 型 '
ms.date: 03/30/2017
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
ms.openlocfilehash: 92be0b3b0fd1212c4254a449f902b85e998aa148
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564314"
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code 組み込み XAML 型 
XAML の運用環境でコードの配置を許可します。 XAML、またはランタイムによって解釈など、後から使用の XAML の運用環境で左側をコンパイルする XAML プロセッサの実装でこのようなコードをコンパイルするか、できます。  
  
## <a name="xaml-object-element-usage"></a>XAML オブジェクト要素の使用方法  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a>コメント  
 内のコード、 `x:Code` XAML ディレクティブ要素が、一般的な XML 名前空間内の解釈のままと XAML 名前空間を指定します。 そのため、必要がある通常を使用するコードを囲む`x:Code`内、`CDATA`セグメント。  
  
 `x:Code` 次の XAML の運用環境のすべての可能な展開メカニズムは許可されません。 特定のフレームワーク (WPF など) でコードをコンパイルする必要があります。 その他のフレームワーク`x:Code`使用状況を通常許可されない可能性があります。  
  
 管理を許可するフレームワーク`x:Code`コンテンツを使用する適切な言語コンパイラ`x:Code`コンテンツは、アプリケーションのコンパイルに使用されるを含むプロジェクトの設定とターゲットによって決まります。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 内で宣言されているコード`x:Code`WPF には、いくつかの重要な制限。  
  
-   `x:Code`ディレクティブ要素は XAML の運用環境のルート要素のすぐ下の子要素である必要があります。  
  
-   [X:class ディレクティブ](../../../docs/framework/xaml-services/x-class-directive.md)親ルート要素に提供する必要があります。  
  
-   コード内に配置`x:Code`は既にその XAML ページに対して作成される部分クラスのスコープ内にあるコンパイルによって処理されます。 したがって、部分クラスのメンバーまたは変数を定義するすべてのコードがあります。  
  
-   以外の場合、部分クラス内のクラスを入れ子にして、追加のクラスを定義することはできません (入れ子可能ですが、XAML で入れ子になったクラスは参照できないために、一般的ではありません)。 既存の部分クラスに使用される名前空間以外の CLR 名前空間を定義またはに追加できません。  
  
-   部分クラスの CLR 名前空間の外部コードのエンティティへの参照する必要がありますすべて完全修飾します。 上書きを部分クラスのオーバーライド可能なメンバーにメンバーが宣言されている場合は、言語固有のオーバーライド キーワードを使用してこれを指定してください。 メンバーが宣言されている場合`x:Code`XAML から作成された部分クラスのメンバーと競合するスコープ、ように、コンパイラが、競合を報告していること、XAML ファイルことはできませんコンパイル、またはロードします。  
  
## <a name="see-also"></a>関連項目  
 [x:Class ディレクティブ](../../../docs/framework/xaml-services/x-class-directive.md)  
 [WPF における分離コードと XAML](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [XAML の概要 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
