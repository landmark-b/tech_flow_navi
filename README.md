# AI Trend Lineage Agent (MVP)

特定の技術分野（例: LLM Scaling Laws）における論文の系譜を自動生成し、
「点」ではなく「線」での技術動向把握を支援するAIエージェントのMVPです。

## 🚀 目的 (Why)
- 新技術のキャッチアップにおいて、個別の論文を読むだけでは歴史的な文脈が見えにくい。
- 論文間の「影響関係」や「進化のポイント」を構造化して提示することで、
  プロダクトマネージャー(PM)やリサーチャーの戦略策定を支援する。

## 🛠 仕組み (Architecture)
1. **Search**: arXiv APIから特定クエリで論文を収集 (Submitted Date順ではなく関連度順)
2. **Embed**: Sentence-Transformersによりタイトル+要約をベクトル化
3. **Lineage**: 時系列 × Cosine類似度により、論文間の親子関係（系譜）を推定
4. **Explain**: LLM (Mock/OpenAI) が親子間の「技術的な進化・差分」を言語化

## 📦 実行方法 (Usage)
本プロジェクトは Google Colab での動作を想定しています。

1. `notebooks/mvp_lineage_agent.ipynb` を Google Colab で開く。
2. 必要なライブラリをインストール (`pip install -r requirements.txt` 相当)。
3. ノートブックを実行すると、JSON形式で系譜データが出力されます。

## 📚 Tech Stack
- Python 3.x
- arXiv API (feedparser)
- sentence-transformers (all-MiniLM-L6-v2)
- scikit-learn (Cosine Similarity)
- OpenAI API (Optional for explanation generation)
