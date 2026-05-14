# Geotechnical AI Assistant (TCVN 10304:2025)

Hệ thống hỗ trợ kỹ sư địa kỹ thuật tra cứu và tính toán theo tiêu chuẩn **TCVN 10304:2025 (Móng cọc)**.

## 🚀 Tính năng chính
- **RAG Engine (FAISS)**: Truy xuất thông tin chính xác từ 124 trang tiêu chuẩn.
- **Symbolic Math**: Tính toán sức chịu tải cọc bằng SymPy, đảm bảo độ chính xác kỹ thuật.
- **Premium UI**: Giao diện Streamlit hiện đại, hỗ trợ hiển thị LaTeX sắc nét.
- **Unified OCR**: Quy trình số hóa tiêu chuẩn từ PDF sang Markdown bằng Gemini 2.0.

## 🏗️ Kiến trúc hệ thống
1. **Dữ liệu**: PDF gốc -> Gemini OCR -> Markdown -> Hierarchical Chunking -> FAISS Index.
2. **Xử lý**: Query -> Vector Search (Sentence Transformers) -> Context -> Gemini 2.0 Flash Lite -> Answer.
3. **Tính toán**: Tích hợp module toán học ký hiệu để kiểm chứng các công thức phức tạp.

## 🛠️ Cài đặt & Khởi chạy
1. **Cài đặt thư viện**:
   ```bash
   uv pip install -r requirements.txt
   ```
2. **Cấu hình API Key**:
   Tạo file `.env` và thêm:
   ```env
   GEMINI_API_KEY=your_api_key_here
   ```
3. **Nạp dữ liệu (Ingestion)**:
   ```bash
   uv run python src/gemini_ingest.py
   uv run python src/load_perfect_chunks.py
   ```
4. **Chạy ứng dụng**:
   ```bash
   uv run streamlit run src/app_streamlit.py
   ```

## 📝 Lưu ý
- Hệ thống sử dụng **FAISS** thay vì ChromaDB để tối ưu hóa hiệu năng và tránh xung đột thư viện trên Windows.
- Mọi câu trả lời cần được kiểm chứng bởi kỹ sư chuyên môn trước khi áp dụng vào thiết kế thực tế.
