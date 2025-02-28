# Usa a imagem oficial do PHP com FPM
FROM php:8.2-fpm

# Instala dependências do sistema e extensões PHP
RUN apt-get update && apt-get install -y \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    zip \
    unzip \
    curl \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd pdo pdo_mysql opcache

# Instala Redis para PHP
RUN pecl install redis && docker-php-ext-enable redis

# Instalar o Composer globalmente
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Verificar se o Composer foi instalado corretamente
RUN composer --version

# Define o diretório de trabalho
WORKDIR /var/www/html

# Copia o restante do projeto
COPY . .

# Corrige permissões para Laravel (caso necessário)
RUN chown -R www-data:www-data /var/www/html/storage /var/www/html/bootstrap/cache || true

# Exibe logs no console
CMD ["php-fpm"]
