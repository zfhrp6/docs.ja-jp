---
title: 仮想メンバー
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa4227fc4476b86f07216650b22fccc25af7dd98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573092"
---
# <a name="virtual-members"></a>仮想メンバー
したがって、サブクラスの動作を変更する、仮想メンバーをオーバーライドできます。 それらは、拡張性の観点からのコールバックを非常に似ていますが、実行のパフォーマンスとメモリ消費量の観点から優れています。 また、仮想メンバーは、特殊な既存の型 (特殊化) の種類を作成する必要があるシナリオで複数な操作です。  
  
 仮想メンバーはコールバックとイベントをよりパフォーマンスが向上しますが、非仮想メソッドをより実行しません。  
  
 仮想メンバーの主な欠点は、仮想メンバーの動作はコンパイル時にのみ変更できます。 実行時に、コールバックの動作を変更できます。  
  
 コールバック (やその他のコールバックより) と同様に、仮想メンバーは、設計、テスト、および仮想メンバーへの呼び出しが予測できない方法でオーバーライドされることができ、任意のコードを実行できるため維持にコストがかかる。 またより多くの労力は通常、設計およびそれらを文書化のコストが高いため、仮想メンバーの契約を明確に定義する要求されます。  
  
 **X しないで**これを行うには相応の理由があり、デザイン、テスト、および仮想メンバーを保守に関連するすべてのコストを認識している限り、メンバーを仮想にすることです。  
  
 仮想メンバーは、互換性の問題なしに作成できる変更の観点からありました。 また、これらはよりも遅い非仮想メンバーは、仮想メンバーへの呼び出しはインライン関数ではないため、ほとんどの場合です。  
  
 **✓ を検討してください**に何がどうしても必要なだけの機能拡張を制限します。  
  
 **✓ しないで**仮想メンバーのアクセシビリティは public で保護されたアクセシビリティを優先します。 パブリック メンバーは拡張機能を提供 (必要な場合) プロテクト仮想メンバーを呼び出すことによってです。  
  
 クラスのパブリック メンバーは、そのクラスの直接のコンシューマーを適切な機能のセットを提供する必要があります。 仮想メンバーは、サブクラスでオーバーライドされるように設計されていて、保護されたアクセシビリティがスコープを使用する場所のすべての仮想機能拡張ポイントを有効にします。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
