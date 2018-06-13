---
title: '&#39;&lt;typename&gt; &#39;から継承できません&lt;型&gt; &#39; &lt;basetypename&gt; &#39;ベースのアクセスを展開しているため&lt;型&gt;。アセンブリの外部'
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: f747b2b24f5fecc22b9e1fbc6ba26b634e9ead2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598425"
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a>&#39;&lt;typename&gt; &#39;から継承できません&lt;型&gt; &#39; &lt;basetypename&gt; &#39;ベースのアクセスを展開しているため&lt;型&gt;。アセンブリの外部
基本クラスからクラスまたはインターフェイスを継承またはインターフェイスが、制限の緩いアクセス レベル。  
  
 たとえば、`Public`インターフェイスから継承、`Friend`インターフェイス、または`Protected`クラスから継承、`Private`クラスです。 これは、基底クラスまたは目的のレベル以外にアクセスするインターフェイスを公開します。  
  
 **エラー ID:** BC30910  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   派生クラスまたはインターフェイスには、少なくとも基底クラスまたはインターフェイスと同程度に制限を指定のアクセス レベルを変更します。  
  
     - または -  
  
-   制限の緩いアクセス レベルを必要とする場合は、削除、`Inherits`ステートメントです。 さらに制限された基底クラスまたはインターフェイスから継承することはできません。  
  
## <a name="see-also"></a>関連項目  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
