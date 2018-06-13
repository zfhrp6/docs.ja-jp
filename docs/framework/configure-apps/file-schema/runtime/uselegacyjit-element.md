---
title: '&lt;useLegacyJit&gt;要素'
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd0ae1a44b41ddcae2149bcf685871a37dd01b06
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746775"
---
# <a name="ltuselegacyjitgt-element"></a>&lt;useLegacyJit&gt;要素

共通言語ランタイムが Just-In-Time コンパイルの従来の 64 ビット JIT コンパイラを使用するかどうかを決定します。  
  
\<configuration>  
\<ランタイム >  
\<useLegacyJit >
  
## <a name="syntax"></a>構文  
  
```xml
<useLegacyJit enabled=0|1 />
```

要素名`useLegacyJit`小文字が区別されます。
  
## <a name="attributes-and-elements"></a>属性と要素

以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
| 属性 | 説明                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | 必須の属性です。<br><br>ランタイムがレガシの 64 ビット JIT コンパイラを使用しているかどうかを指定します。 |  
  
### <a name="enabled-attribute"></a>enabled 属性  
  
| [値] | 説明                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| 0     | 共通言語ランタイムは、.NET Framework 4.6 およびそれ以降のバージョンに含まれる新しい 64 ビット JIT コンパイラを使用します。 |  
| 1     | 共通言語ランタイムは、以前の 64 ビット JIT コンパイラを使用します。                                                     |  
  
### <a name="child-elements"></a>子要素

なし
  
### <a name="parent-elements"></a>親要素  
  
| 要素         | 説明                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | 共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。 |  
| `runtime`       | ランタイム初期化オプションに関する情報を含んでいます。                                                        |  
  
## <a name="remarks"></a>コメント  

.NET Framework 4.6 以降では、共通言語ランタイム新しい 64 ビットのコンパイラの Just-In-Time (JIT) コンパイル既定で使用します。 場合によっては、以前のバージョンの 64 ビット JIT コンパイラが JIT でコンパイルされたアプリケーション コードからの動作の違いにあります。 設定して、`enabled`の属性、`<useLegacyJit>`要素`1`、新しい 64 ビット JIT コンパイラを無効にし、代わりに、従来の 64 ビット JIT コンパイラを使用して、アプリをコンパイルすることができます。  
  
> [!NOTE]
> `<useLegacyJit>`要素が 64 ビット JIT コンパイルのみに影響します。 32 ビット JIT コンパイラによるコンパイルには影響しません。  
  
構成ファイルの設定を使用する代わりにその他の 2 つの方法では、レガシの 64 ビット JIT コンパイラを有効にすることができます。  
  
- 環境変数の設定

  設定、`COMPLUS_useLegacyJit`いずれかのように環境変数`0`(新しい 64 ビット JIT コンパイラを使用) または`1`(古い 64 ビット JIT コンパイラを使用)。
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  環境変数が*グローバル スコープ*コンピューター上のすべてのアプリケーションを実行に影響を与えることを意味します。 かどうか設定をオーバーライドできますアプリケーション構成ファイルの設定をします。 環境変数の名前は区別されません。
  
- レジストリ キーを追加します。

  追加することで、従来の 64 ビット JIT コンパイラを有効にすることができます、`REG_DWORD`するか、値、`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework`または`HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework`レジストリのキー。 値が名前付き`useLegacyJit`します。 値が 0 の場合、新しいコンパイラが使用されます。 値が 1 の場合は、従来の 64 ビット JIT コンパイラは有効です。 レジストリ値の名前は区別されません。
  
  値を追加する、`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework`キー、マシンで実行されているすべてのアプリに影響します。 値を追加する、`HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework`キーが現在のユーザーが実行するすべてのアプリに影響します。 コンピューターが複数のユーザー アカウントを使って構成されている場合のみアプリ現在のユーザーが実行には影響、他のユーザーを同様のレジストリ キーに値を追加しない限り、します。 追加する、`<useLegacyJit>`存在である場合、構成ファイルに要素が、レジストリ設定をオーバーライドします。  
  
## <a name="example"></a>例  

次の構成ファイルでは、新しい 64 ビット JIT コンパイラでコンパイルを無効になり、代わりに、従来の 64 ビット JIT コンパイラを使用します。  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

[\<ランタイム > 要素](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)   
[\<configuration > 要素](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)   
[軽減策: 新しい 64 ビット JIT コンパイラ](../../../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)
