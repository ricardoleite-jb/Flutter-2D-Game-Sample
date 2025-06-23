FROM debian:bookworm-slim

# Install system dependencies for Flutter Web/Linux
RUN apt-get update && apt-get install -y --no-install-recommends \
  curl \
  git \
  unzip \
  xz-utils \
  zip \
  ca-certificates \
  build-essential \
  clang \
  cmake \
  ninja-build \
  pkg-config \
  libgtk-3-dev \
  libglib2.0-dev \
  libgstreamer1.0-dev \
  libgstreamer-plugins-base1.0-dev \
  && rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/flutter/flutter.git /usr/local/flutter

# Set flutter environment path
ENV PATH="/usr/local/flutter/bin:/usr/local/flutter/bin/cache/dart-sdk/bin:${PATH}"

# Precache tools
RUN flutter precache --web --linux && flutter doctor -v

# Set working directory
#WORKDIR /app

# Optional: uncomment to copy and resolve pub dependencies during image build
# COPY pubspec.* ./
# RUN flutter pub get

# This image expects app volume mounting, so no CMD