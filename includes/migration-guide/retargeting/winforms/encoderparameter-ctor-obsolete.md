### <a name="encoderparameter-ctor-is-obsolete"></a>EncoderParameter ctor が廃止に

|   |   |
|---|---|
|説明|<xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> コンストラクターは廃止され、使用された場合、ビルド警告が発生します。|
|提案される解決策|コンストラクター <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> は引き続き動作しますが、.NET 4.5 のツールでコードを再コンパイルするときに古いビルド警告を回避するには、コンストラクター <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)> を代わりに使用する必要があります。|
|スコープ|マイナー|
|Version|4.5|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|

