import streamlit as st
import pandas as pd

st.set_page_config(page_title="ODS Algoritma Karşılaştırma", layout="wide")

@st.cache_data
def load_data():
    return pd.read_excel("ods_comparison.xlsx")

df = load_data()

st.title("ODS Algoritma Karşılaştırma Aracı")
st.write("ODS algoritmasının kararlarını kullanıcı onaylarıyla karşılaştırmak için hazırlanan arayüz.")

for i, row in df.iterrows():
    st.subheader(f"Numune ID: {row['id']}")
    st.write(f"İstemi Yapan Birim: {row['unit']}")
    st.write(f"Tanı: {row['dx']}")
    st.write(f"ODS Algoritma Kararı: **{row['ods_decision']}**")
    st
