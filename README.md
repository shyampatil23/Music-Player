# Music-Player

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity"
    android:background="@drawable/icon4">


    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_marginLeft="30dp">

        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/tv_title"
            android:text="Now Playing"
            android:textSize="18sp"
            android:textColor="@color/purple_500"
            android:textStyle="bold"
            android:layout_marginTop="20dp"
            android:fontFamily="sans-serif-condensed-medium"/>


        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/tv_songname"
            android:text="The Kid Laroi,Justin Bieber-Stay"
            android:textSize="14sp"
            android:textColor="@color/black"
            android:textStyle="bold"
            android:layout_marginTop="20dp"
            android:layout_marginLeft="10dp"
            android:fontFamily="sans-serif-condensed-medium"/>

    </LinearLayout>
    <ImageView
        android:id="@+id/audio_imageview"
        android:layout_width="match_parent"
        android:layout_height="400dp"
        android:layout_gravity="center"
        android:layout_marginTop="60dp"
        android:src="@drawable/img" />
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="40dp"
        android:id="@+id/layout_seekbar"
        android:orientation="vertical"
        android:layout_below="@+id/audio_imageview"
        android:gravity="center_vertical"
        android:layout_marginStart="5dp"
        android:layout_marginEnd="5dp"
        android:layout_marginTop="10dp">

        <SeekBar
            android:layout_width="match_parent"
            android:layout_height="40dp"
            android:id="@+id/audio_seekbar"
            android:layout_weight="1"/>
        <LinearLayout
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:orientation="horizontal"
            android:layout_margin="5dp">
            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:id="@+id/player_position"
                android:text="00.00"
                android:textSize="15dp"
                android:textColor="@color/black"
                android:textStyle="bold"
                android:textAlignment="viewStart"
                android:layout_weight="1"/>
            <TextView
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:id="@+id/player_duration"
                android:text="00.00"
                android:textSize="15dp"
                android:textColor="@color/black"
                android:textStyle="bold"
                android:layout_weight="1"
                android:textAlignment="viewEnd"/>
        </LinearLayout>
    </LinearLayout>
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="50dp"
        android:id="@+id/buttons"
        android:orientation="horizontal"
        android:gravity="center_vertical"
        android:layout_below="@+id/layout_seekbar"
        android:layout_marginTop="10dp"
        android:layout_marginStart="5dp"
        android:layout_marginEnd="5dp">
        <ImageView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:src="@drawable/backward"
            android:id="@+id/backward"
            android:layout_weight="1"/>
        <ImageView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:src="@drawable/ic_play"
            android:id="@+id/play"
            android:layout_weight="1" />
        <ImageView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:src="@drawable/ic_pause"
            android:id="@+id/pause"
            android:visibility="gone"
            android:layout_weight="1" />
        <ImageView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/forward"
            android:src="@drawable/icforward"
            android:layout_weight="1" />
    </LinearLayout>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="50dp"
        android:orientation="horizontal"
        android:gravity="center_vertical"
        android:layout_below="@+id/buttons"
        android:layout_marginTop="10dp"
        android:layout_marginStart="5dp"
        android:layout_marginEnd="5dp">
        <ImageView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:src="@drawable/ic_loop"
            android:id="@+id/loop"
            android:layout_weight="1"/>
        <ImageView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:src="@drawable/ic_cut"
            android:id="@+id/cutSong"
            android:layout_weight="1" />
        <ImageView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/favourite"
            android:src="@drawable/ic_baseline_favorite_border_24"
            android:layout_weight="1" />
        <ImageView
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:id="@+id/shuffle"
            android:src="@drawable/ic_shuffle"
            android:layout_weight="1" />
    </LinearLayout>
</RelativeLayout>
