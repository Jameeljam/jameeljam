import streamlit as st
import helper
import matplotlib.pyplot as plt
import seaborn as sns

st.sidebar.title("Whatsapp Chat Analysis and Sentiment Analysis") 
uploaded_file = st.sidebar.file_uploader("/Users/jammy/Downloads/WhatsApp Chat with MSC DS 22-24(Will Be Employed💥).txt")
if uploaded_file is not None:  
# To read file as bytes:
    bytes_data = uploaded_file.getvalue() 
    file = bytes_data.decode("utf-8") 
    key = '12hr'
    df = model1(file)
    print(df)
    st.dataframe(df)

    user_list = df['user'].unique().tolist() 
    user_list.remove('group_notification') 
    user_list.sort() 
    user_list.insert(0,"Overall",)
    selected_user = st.sidebar.selectbox("show analysis",user_list)
    st.sidebar.title("Whatsapp Chat Analysis and Sentiment Analysis") 
uploaded_file = st.sidebar.file_uploader("/Users/jammy/Downloads/WhatsApp Chat with MSC DS 22-24(Will Be Employed💥).txt")
if uploaded_file is not None:  
# To read file as bytes:
    bytes_data = uploaded_file.getvalue() 
    file = bytes_data.decode("utf-8") 
    key = '12hr'
    df = model1(file)
    print(df)
    st.dataframe(df)

    user_list = df['user'].unique().tolist() 
    user_list.remove('group_notification') 
    user_list.sort() 
    user_list.insert(0,"Overall",)
    selected_user = st.sidebar.selectbox("show analysis",user_list)
    if st.sidebar.button("Show Analysis"):
    num_msg, word, num_media, num_links = helper.fetch_stats(selected_user, df) 
    col1, col2, col3, col4 = st.columns(4)
    with col1:
        st.header("Total Messages") 
        st.title(num_msg)
    with col2:
        st.header("Total words") 
        st.title(word)
    with col3:
        st.header("Media Shared") 
        st.title(num_media)
    with col4:
        st.header("Links Shared") 
        st.title(num_links)

    # monthly timeline 
    st.title("Monthly Timeline")
    timeline = helper.monthly_timeline(selected_user, df) 
    fig, ax = plt.subplots()
    ax.plot(timeline['time'], timeline['message'], color='green') 
    plt.xticks(rotation='vertical')
    st.pyplot(fig)

    # Daily Timeline 
    st.title("Daily Timeline")
    daily_time = helper.daily_timeline(selected_user, df) 
    fig, ax = plt.subplots()
    ax.plot(daily_time['date'], daily_time['message'], color='black') 
    plt.xticks(rotation='vertical')
    st.pyplot(fig)

    # activity map 
    st.title("Activity Map")
    col1, col2 = st.columns(2)

    with col1:
        st.header('Most Busy Day')
        busy_day = helper.week_activity(selected_user, df) 
        fig, ax = plt.subplots() 
        ax.bar(busy_day.index, busy_day.values) 
        plt.xticks(rotation='vertical')
        st.pyplot(fig)

    with col2:
        st.header('Most Busy Month')
        busy_month = helper.month_activity(selected_user, df) 
        fig, ax = plt.subplots()
        ax.bar(busy_month.index, busy_month.values, color='orange') 
        plt.xticks(rotation='vertical')
        st.pyplot(fig)

# Activity Heatmap
st.title('Weekly Acitivity HeatMap')
activity_hm = helper.activity_heatmap(selected_user,df) 
fig, ax = plt.subplots()
ax = sns.heatmap(activity_hm) 
st.pyplot(fig)

#emoji
emoji_df = helper.emoji_helper(selected_user, df) 
st.title("Emoji Analysis")
col1, col2 = st.columns(2) 

with col1:
    st.dataframe(emoji_df)

with col2:
    fig, ax = plt.subplots() 
    ax.pie(emoji_df[1].head(), autopct="%0.2f") 
    st.pyplot(fig)
